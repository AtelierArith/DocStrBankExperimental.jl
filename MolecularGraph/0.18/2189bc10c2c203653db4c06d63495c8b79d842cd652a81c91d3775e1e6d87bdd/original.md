```
ring_count(mol::MolGraph) -> Vector{Int}
```

Return a vector of size $n$ representing the number of [`sssr`](@ref) that 1 to $n$th atoms of the given molecule belong to.

This property corresponds to SMARTS `R` query.
