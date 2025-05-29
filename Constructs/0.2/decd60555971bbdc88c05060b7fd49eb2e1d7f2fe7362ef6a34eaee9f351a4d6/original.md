```
PrimitiveIO(T) -> Construct{T}
```

Defines a primitive IO construct for `type` based on [`read`](https://docs.julialang.org/en/v1.6/base/io-network/#Base.read) and [`write`](https://docs.julialang.org/en/v1.6/base/io-network/#Base.write).

This is the default construct for `Bool`, `Char`, `UInt8`, `UInt16`, `UInt32`, `UInt64`, `UInt128`, `Int8`, `Int16`, `Int32`, `Int64`, `Int128`, `Float16`, `Float32` and `Float64`.

# Examples

```jldoctest
julia> serialize(PrimitiveIO(Complex{Bool}), im)
2-element Vector{UInt8}:
 0x00
 0x01
```
