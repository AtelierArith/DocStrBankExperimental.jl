```
MixedCellIterator(support:Vector{<:Matrix}, lifting::Vector{<:Vector{<:Integer}})
```

Returns an iterator over all (fine) mixed cells of the given `support` induced by the given `lifting`. If the lifting is not sufficiently generic the mixed cells induced by a sligtly perturbated lifting are computed. The iterator returns in each iteration a [`MixedCell`](@ref). Note that due to efficiency reason the same object is returned in each iteration, i.e., if you want to store the computed cells you need to make a `copy`. Alternatively you can also use [`mixed_cells`](@ref) to compute all mixed cells.
