```
adjust_crc!(crc, a::AbstractVector{UInt8}, wantcrc::UInt32, fixpos::Integer)
```

Write 4 bytes to `a[fixpos:fixpos+3]` so that `crc(a)` becomes equal to `wantcrc`. This is especially useful if you want to store the checksum of some data *within the data* itself, or simply to set the crc to an arbitrary predetermined value. Here, `crc` is a function that computes a 32-bit CRC checksum: either `crc32c` from the `CRC32c` standard library or `crc32` from the [CRC32.jl package](https://github.com/JuliaIO/CRC32.jl).

Note that the `adjust_crc!` function is most efficient when `fixpos` is close to the end of the array `a`, and is slowest for `fixpos` near the beginning. (Though in all cases the cost should scale linearly with `length(a)`.) See also [`adjust_crc`](@ref) to append similar padding bytes to the end of a file or I/O stream (which has the advantage of not requiring you to read the entire file into memory at once).
