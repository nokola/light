# Light

An operating system in Rust using blog_os tutorials, see https://github.com/phil-opp/blog_os.

## Build
First time:
```
rustup override add nightly
rustup component add rust-src
cargo install cargo-xbuild
cargo install bootimage --version "^0.7.7"
rustup component add llvm-tools-preview
```

Then:
```
cargo bootimage
```
The OS image will be in `target\x86_64-light\debug\bootimage-light.bin`

Note: To build OS image run `cargo xbuild`

## Running
To run, use [QEMU](https://www.qemu.org/) or USB stick.

QEMU, Windows PowerShell:
```
& "C:\Program Files\qemu\qemu-system-x86_64.exe" --drive format=raw,file=target/x86_64-light/debug/bootimage-light.bin
```

QEMU, Linux:
```
qemu-system-x86_64 -drive format=raw,file=target/x86_64-light/debug/bootimage-light.bin
```

USB stick, Linux:
```
dd if=target/x86_64-blog_os/debug/bootimage-blog_os.bin of=/dev/sdX && sync
```
Replace `sdX` with your USB stick device name. **Be careful** to choose the correct device, because everything on it will be overwritten.

## More Info 
Based on blog_os tutorial: [Minimal Rust Kernel](https://os.phil-opp.com/minimal-rust-kernel/)

## License

This project is licensed under either of

* Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0))
* MIT license ([LICENSE-MIT](LICENSE-MIT) or [http://opensource.org/licenses/MIT](http://opensource.org/licenses/MIT))

at your option.
