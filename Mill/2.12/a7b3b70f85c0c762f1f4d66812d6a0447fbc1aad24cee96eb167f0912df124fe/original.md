```
ScatteredBags(k::Vector{<:Integer})
```

Construct a new [`ScatteredBags`](@ref) struct from `Vector` `k` specifying the index of the bag each instance belongs to.

# Examples

```jldoctest
julia> ScatteredBags([2, 2, 1, 1, 1, 3])
ScatteredBags{Int64}([[3, 4, 5], [1, 2], [6]])
```
