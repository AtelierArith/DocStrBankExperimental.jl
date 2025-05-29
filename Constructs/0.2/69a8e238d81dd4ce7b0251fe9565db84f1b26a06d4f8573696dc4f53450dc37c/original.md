```
Sequence(Ts|elements...) -> Construct{Tuple{Ts...}}
```

Defines the sequence of construct data based on `elements`.

This is the default constructor for `Tuple{Ts...}`.

# Examples

```jldoctest
julia> serialize((true, 0x23))
2-element Vector{UInt8}:
 0x01
 0x23

julia> deserialize(Sequence(Bool, UInt8), b"\xab\xcd")
(true, 0xcd)
```

# Known problems

In Julia 1.6, if the number of `Sequence` elements is greater than 9, [`@construct`](@ref) cannot deduce the field type correctly.
