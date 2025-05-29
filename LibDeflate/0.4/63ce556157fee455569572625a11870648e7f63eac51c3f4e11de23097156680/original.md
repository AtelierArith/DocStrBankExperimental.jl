```
crc32(data, start=UInt32(0))::UInt32
```

Calculate the crc32 checksum of `data` and seed `start` (0 by default). Note that crc32 is a different and slower algorithm than the `crc32c` provided in the Julia standard library.

See also: [`unsafe_crc32`](@ref)
