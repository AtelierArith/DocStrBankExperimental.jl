```
retrieve_symmetries(pge::PeriodicGraphEmbedding3D{T}, eqs::AbstractVector{S}=pge.cell.equivalents, vtypes=nothing, check_symmetry=check_valid_symmetry) where {T,S}
```

Return a `(symgroup, discarded)` where `symgroup` is a [`SymmetryGroup3D`](@ref) which stores the list of symmetry operations on the graph embedding. These symmetry operations are taken from the list of [`EquivalentPosition`](@ref) `eqs`, defaulting to those specified in the [`Cell`](@ref) of the graph embedding. `discarded` is the list of indices `i` such that the operation `eqs[i]` could not be mapped to an actual symetry of the periodic graph, and was thus discarded.

See [`find_symmetries`](@ref) to automatically determine the symmetries, and for the definition of the `vtypes` and `check_symmetry` arguments.
