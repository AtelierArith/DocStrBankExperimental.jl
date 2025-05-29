```
unpack(bytes::Vector{UInt8}, T::Type [, ctx::Context])::T
unpack(bytes::Vector{UInt8}, T::Type [, fmt::Format, ctx:::Context])::T
unpack(io::IO, T::Type, args...)::T
```

Unpack a binary msgpack representation of a value of type `T` in format `fmt` from a byte vector `bytes` or a stream `io`. The returned value is guaranteed to be of type `T`.

If no format is provided, it is derived from `T` via `format(T, ctx)`. The context `ctx` defaults to [`context`](@ref).
