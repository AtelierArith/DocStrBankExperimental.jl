```
connectivity(mol::SimpleMolGraph) -> Vector{Int}
```

Return a vector of size $n$ representing the number of total atoms (implicit and explicit) connected to 1 to $n$th atoms of the given molecule.

This property corresponds to SMARTS `X` query.
