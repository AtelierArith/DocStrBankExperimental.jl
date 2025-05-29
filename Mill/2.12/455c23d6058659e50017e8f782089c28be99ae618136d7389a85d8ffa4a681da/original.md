```
AlignedBags(bags::UnitRange{<:Integer}...)
```

Construct a new [`AlignedBags`](@ref) struct from bags in arguments.

# Examples

```jldoctest
julia> AlignedBags(1:3, 4:8)
AlignedBags{Int64}(UnitRange{Int64}[1:3, 4:8])
```
