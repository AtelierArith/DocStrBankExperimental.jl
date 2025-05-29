```
pack(x)
```

Serialize `x` to MessagePack format and return the resulting `Vector{UInt8}`.

This function uses [`msgpack_type`](@ref) and [`to_msgpack`](@ref) to determine the appropriate translation of the `value` into MessagePack format.

See also: [`unpack`](@ref)
