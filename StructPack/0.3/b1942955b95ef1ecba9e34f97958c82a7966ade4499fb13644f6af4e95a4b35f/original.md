```
pack(value, [, ctx::Context])::Vector{UInt8}
pack(value, [, fmt::Format, ctx::Context])::Vector{UInt8}
pack(io::IO, args...)::Nothing
```

Create a binary msgpack representation of `value` according to the given format `fmt`. If a stream `io` is passed, the representation is written into it.

If no format is provided, it is derived from the type of `value` via `format(typeof(value), ctx)`. The context defaults to the value of [`context`](@ref), which is a scoped value in julia 1.11 or newer and a reference else.

If both a format and a context is provided, `fmt` is used for packing `value` while `ctx` is passed along to deeper packing related calls.
