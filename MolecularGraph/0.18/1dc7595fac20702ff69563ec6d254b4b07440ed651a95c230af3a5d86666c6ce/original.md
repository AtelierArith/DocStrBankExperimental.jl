```
smallest_ring(mol::SimpleMolGraph) -> Vector{Int}
```

Return a vector of size $n$ representing the size of the smallest [`sssr`](@ref) that 1 to $n$th atoms of the given molecule belong to. 

If the node is not in a ring, the value would be 0. This property corresponds to SMARTS `r` query.
