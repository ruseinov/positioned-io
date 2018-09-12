positioned-io
=============

This crate allows you to specify an offset for reads and writes, without changing the current
position in a file. This is similar to [`pread()` and `pwrite()`][pread] in C.

The major advantages of this type of I/O are:

* You don't need to seek before doing a random-access read or write, which is convenient.
* Reads don't modify the file at all, so don't require mutability.

[pread]: http://man7.org/linux/man-pages/man2/pread.2.html

[![Build Status](https://travis-ci.org/vasi/positioned-io.svg?branch=master)](https://travis-ci.org/vasi/positioned-io)
[![Crates.io](https://img.shields.io/crates/v/positioned-io.svg)](https://crates.io/crates/positioned-io)
[![Documentation](https://docs.rs/positioned-io/badge.svg)](https://docs.rs/positioned-io)

Example
-------

Read the fifth 512-byte sector of a file:

```rust
use positioned_io::ReadAt;

// Note that file does not need to be mut!
let file = File::open("foo.data")?;
let mut buf = vec![0; 512];
let bytes_read = file.read_at(2048, &mut buf)?;
```

Documentation
-------------

https://docs.rs/positioned-io

Usage
-----

Add `positioned-io` to your `Cargo.toml` like so:

```toml
[dependencies]
positioned-io = "0.2"
```

License
-------

positioned-io is licensed under the [MIT license](https://github.com/vasi/positioned-io/blob/master/LICENSE-MIT).
