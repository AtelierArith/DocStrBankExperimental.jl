```
which_fused_ring(mol::SimpleMolGraph) -> Vector{Vector{Int}}
```

Return a vector of size $n$ representing [`fused_rings`](@ref) membership of 1 to $n$th atoms of the given molecule.

Fused ring membership is represented as a set of fused ring indices assigned to each fused rings. This means atoms that have the same fused ring index belong to the same fused ring.
