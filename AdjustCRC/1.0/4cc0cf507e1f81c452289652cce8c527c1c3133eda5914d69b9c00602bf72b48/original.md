```
adjust_crc(crc, filename::AbstractString, wantcrc::UInt32)
adjust_crc(crc, io::IO, wantcrc::UInt32)
```

Write 4 bytes of "padding" to the *end* of the the I/O stream `io` (which *must* be seekable and read/write) or the file `filename`, in order to cause the `crc` checksum of the whole stream/file to equal `wantcrc`. Here, `crc` is a function that computes a 32-bit CRC checksum: either `crc32c` from the `CRC32c` standard library or `crc32` from the [CRC32.jl package](https://github.com/JuliaIO/CRC32.jl).

(This is mainly useful if you want to store the checksum of the file *within the file*: simply set `wantcrc` to be an arbitrary number, such as `rand(UInt32)`, store it within the file as desired, and then call `adjust_crc` to write padding bytes that force the checksum to match `wantcrc`.  Even more simply, you could force all of your files to have a checksum that matches a hard-coded value like `0x01020304`, in which case you don't need to store the checksum in the file itself.) See also [`adjust_crc!`](@ref) to write similar padding bytes to an arbitrary position within an array.
