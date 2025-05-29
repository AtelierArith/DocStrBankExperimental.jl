```
unpack(msgpack_byte_stream::IO, T::Type = Any; strict::Tuple=())
```

Return the Julia value of type `T` deserialized from `msgpack_byte_stream`.

`T` is assumed to have valid [`msgpack_type`](@ref) and [`from_msgpack`](@ref) definitions.

If `msgpack_type(T) === AnyType()`, `unpack` will deserialize the next MessagePack object from `msgpack_byte_stream` into the default Julia representation corresponding to the object's MessagePack type. For details on default Julia representations, see [`AbstractMsgPackType`](@ref).

The `strict` keyword argument is a `Tuple` of `DataType`s where each element `S` must obey `msgpack_type(S) === StructType()`. `unpack` will assume that encountered MessagePack Maps to be deserialized to e.g. `S` will always contain fields that correspond strictly to the fields of `S`. In other words, the `i`th key in the Map must correspond to `fieldname(S, i)`, and the `i`th value must correspond to `getfield(::S, i)`.

See also: [`pack`](@ref), [`construct`](@ref)
