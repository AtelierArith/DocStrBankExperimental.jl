```
encode(d::AbstractProtoDecoder, x::T) where {T}
```

Encode struct `x` of type `T` as protobuf message to `IO` wrapped by `AbstractProtoEncoder`.

For general structs, these methods should be generated using the [`protojl`](@ref) function.
