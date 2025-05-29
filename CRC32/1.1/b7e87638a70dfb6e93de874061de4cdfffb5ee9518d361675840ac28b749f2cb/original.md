```
crc32(data, crc::UInt32=0x00000000)
```

Compute the CRC-32 checksum (ISO 3309, ITU-T V.42, CRC-32-IEEE) of the given `data`, which can be an `Array{UInt8}`, a contiguous subarray thereof, an `AbstractVector{UInt8}`, or a `String`. Optionally, you can pass a starting `crc` integer to be mixed in with the checksum. The `crc` parameter can be used to compute a checksum on data divided into chunks: performing `crc32(data2, crc32(data1))` is equivalent to the checksum of `[data1; data2]`.

There is also a method `crc32(io, nb, crc)` to checksum `nb` bytes from a stream `io`, or `crc32(io, crc)` to checksum all the remaining bytes. Hence you can do [`open(crc32, filename)`](@ref) to checksum an entire file, or `crc32(seekstart(buf))` to checksum an [`IOBuffer`](@ref) without calling [`take!`](@ref).

For a `String`, note that the result is specific to the UTF-8 encoding (a different checksum would be obtained from a different Unicode encoding).
