```
length2bags(ls::Vector{<:Integer})
```

Convert lengths of bags given in `ls` to [`AlignedBags`](@ref) with contiguous blocks.

# Examples

```jldoctest
julia> length2bags([1, 3, 2])
AlignedBags{Int64}(UnitRange{Int64}[1:1, 2:4, 5:6])
```

See also: [`AlignedBags`](@ref).
