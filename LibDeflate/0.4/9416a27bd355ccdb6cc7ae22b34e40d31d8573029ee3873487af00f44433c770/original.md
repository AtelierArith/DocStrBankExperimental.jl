```
unsafe_crc32(in_ptr::Ptr, n_in::Integer, start::UInt32)::UInt32
```

Calculate the crc32 checksum of the first `n_in` bytes of the pointer `in_ptr`, with seed `start` (default is 0). Note that crc32 is a different and slower algorithm than the `crc32c` provided in the Julia standard library.

See also: [`crc32`](@ref)
