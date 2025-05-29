```
unpack(bytes::Vector{UInt8})::Any
unpack(io::IO)::Any
```

Unpack a binary msgpack value via the special format [`AnyFormat`](@ref). The returned value can be of any type.
