```
Overwrite(T, value::T) -> Construct{T}
Overwrite(T, getter) -> Construct{T}
Overwrite(subcon::Construct{T}, value::T) -> Construct{T}
Overwrite(subcon::Construct{T}, getter) -> Construct{T}
```

Overwrite the value when serializing from `getter`/`value`. Deserialization simply passes down.

# Arguments

  * `subcon::Construct{T}`: the underlying construct.
  * `value::T`: the value to overwrite when serializing.
  * `getter`: the function to overwrite when serializing. the function should have signature like `(::T; contextkw...)` and satisfies idempotence (`getter(getter(x)) == getter(x)`).

# Examples

```jldoctest
julia> serialize(Overwrite(UInt8, 0x01), 2)
1-element Vector{UInt8}:
 0x01

julia> serialize(Overwrite(Int8, abs), -2)
1-element Vector{UInt8}:
 0x02

julia> deserialize(Overwrite(UInt8, 0x01), b"\x05")
0x05
```
