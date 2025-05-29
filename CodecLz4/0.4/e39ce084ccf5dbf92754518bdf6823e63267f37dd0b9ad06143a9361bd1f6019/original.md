```
lz4_hc_compress(input::Union{Vector{UInt8},Base.CodeUnits{UInt8}}, acceleration::Integer=9)
```

Compresses `input` using LZ4*compress*HC. Returns a Vector{UInt8} of the compressed data.
