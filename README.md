# Messing around with executables

This is meant for exploring what happens when the bytes of an executable are manipulated (after the program has been compiled).
I'm using the default rust binary project to get started and trying out varying manipulations on the different OSes I have access to.

All executables are compiled as `cargo build --release`, then modified, then run as `cargo run` or the file itself is directly called.

## Windows

### Simple text find and replace
- When using nvim, `:%s/world!/hacked` and saving will result in an executable binary that prints `hello, hacked` instead of `hello, world!`.
- Adding an extra character such as `:s/world!/hacked!` will result in an error when running `(exit code: 0xc0000005, STATUS_ACCESS_VIOLATION)`
- Removing a character such as `%s/world!/hacke` will result in an error when running `(exit code: 0xc000007b)`
- So far, `cargo run --release` will reveal the error codes in terminal, while running the `.exe` directly will cause an OS modal to pop up.
