```
unpack(bytes::Vector{UInt8})::Any
unpack(io::IO)::Any
```

特別なフォーマット [`AnyFormat`](@ref) を介してバイナリ msgpack 値をアンパックします。返される値は任意の型である可能性があります。
