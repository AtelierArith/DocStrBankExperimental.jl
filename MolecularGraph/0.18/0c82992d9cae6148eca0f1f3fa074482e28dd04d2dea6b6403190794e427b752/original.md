```
which_ring(mol::SimpleMolGraph) -> Vector{Vector{Int}}
```

Return a vector of size $n$ representing [`sssr`](@ref) membership of 1 to $n$th nodes of the given graph.

SSSR membership is represented as a vector of SSSR indices assigned to each rings. This means nodes that have the same SSSR index belong to the same SSSR.
