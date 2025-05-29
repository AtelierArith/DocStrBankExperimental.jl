```
edge_which_ring(mol::SimpleMolGraph) -> Vector{Vector{Int}}
```

Return a vector of size $n$ representing [`sssr`](@ref) membership of 1 to $n$th bonds of the given molecule.

SSSR membership is represented as a set of SSSR indices assigned to each rings. This means bonds that have the same SSSR index belong to the same SSSR.
