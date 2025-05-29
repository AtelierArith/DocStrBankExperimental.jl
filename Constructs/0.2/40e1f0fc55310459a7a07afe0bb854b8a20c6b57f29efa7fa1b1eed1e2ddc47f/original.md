```
Const([T|subcon], value::T) -> Construct{T}
```

Defines a constant `value`, usually used for file headers.

# Arguments

  * `subcon::Construct{T}`: the underlying construct.
  * `value::T`: the expected value.

# Examples

```jldoctest
julia> serialize(Const(0x01), 0x01)
1-element Vector{UInt8}:
 0x01

julia> deserialize(Const(0x01), b"\x01")
0x01
```

```jldoctest
julia> serialize(Const(0x01), 0x03)
ERROR: ValidationError: 3 mismatch the const value 1.
[...]

julia> deserialize(Const(0x01), b"\x02")
ERROR: ValidationError: 2 mismatch the const value 1.
[...]
```
