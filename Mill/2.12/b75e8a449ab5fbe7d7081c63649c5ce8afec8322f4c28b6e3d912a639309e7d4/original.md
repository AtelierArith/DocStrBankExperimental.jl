```
remapbags(b::AbstractBags, idcs::VecOrRange{<:Integer}) -> (rb, I)
```

Select a subset of bags in `b` corresponding to indices `idcs` and remap instance indices appropriately. Return new bags `rb` as well as a `Vector` of remapped instances `I`.

# Examples

```jldoctest
julia> remapbags(AlignedBags([1:1, 2:3, 4:5]), [1, 3])
(AlignedBags{Int64}(UnitRange{Int64}[1:1, 2:3]), [1, 4, 5])

julia> remapbags(ScatteredBags([[1,3], [2], Int[]]), [2])
(ScatteredBags{Int64}([[1]]), [2])
```
