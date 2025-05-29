```
lz4_compress(input::Union{Vector{UInt8},Base.CodeUnits{UInt8}}, acceleration::Integer=0)
```

Compresses `input` using LZ4*compress*fast. Returns a Vector{UInt8} of the compressed data.
