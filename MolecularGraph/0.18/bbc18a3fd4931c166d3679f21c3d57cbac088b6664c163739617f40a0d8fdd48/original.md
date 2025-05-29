```
explicit_hydrogens(mol::SimpleMolGraph) -> Vector{Int}
```

Return a vector of size $n$ representing the number of explicit hydrogens connected to 1 to $n$th atoms of the given molecule.

"Explicit" means hydrogens are explicitly represented as graph nodes.
