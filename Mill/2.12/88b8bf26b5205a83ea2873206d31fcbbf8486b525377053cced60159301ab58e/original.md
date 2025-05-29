```
AlignedBags(k::Vector{<:Integer})
```

Construct a new [`AlignedBags`](@ref) struct from `Vector` `k` specifying the index of the bag each instance belongs to. Throws `ArgumentError` if this is not possible.

# Examples

```jldoctest
julia> AlignedBags([1, 1, 2, 2, 2, 4])
AlignedBags{Int64}(UnitRange{Int64}[1:2, 3:5, 0:-1, 6:6])
```
