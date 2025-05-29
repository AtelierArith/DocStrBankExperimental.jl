```
lz4_decompress(input::Union{Vector{UInt8},Base.CodeUnits{UInt8}}, expected_size::Integer=input.size * 2)
```

Decompresses `input` using LZ4*decompress*safe. `expected_size` must be equal to or larger than the expected decompressed size of the input or decompression will fail. Returns a Vector{UInt8} of the decompressed data.
