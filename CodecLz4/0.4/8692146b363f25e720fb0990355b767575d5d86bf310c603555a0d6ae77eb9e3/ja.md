```
lz4_compress(input::Union{Vector{UInt8},Base.CodeUnits{UInt8}}, acceleration::Integer=0)
```

`input`をLZ4*compress*fastを使用して圧縮します。圧縮されたデータのVector{UInt8}を返します。
