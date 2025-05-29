```
decode(d::AbstractProtoDecoder, ::Type{T}) where {T}
```

Decode a protobuf message from `IO` wrapped by `AbstractProtoDecoder` into s struct of type T.

For general structs, these methods should be generated using the [`protojl`](@ref) function.
