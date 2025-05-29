```
mixed_cells(support::Vector{<:Matrix}, lifting::Vector{<:Vector})
```

Compute all (fine) mixed cells of the given `support` induced by the given `lifting`. If the lifting is not sufficiently generic the mixed cells induced by a sligtly perturbated lifting are computed. The mixed cells are stored as a [`MixedCell`](@ref).
