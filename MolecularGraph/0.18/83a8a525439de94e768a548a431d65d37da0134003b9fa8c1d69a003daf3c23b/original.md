```
implicit_hydrogens(mol::SimpleMolGraph) -> Vector{Int}
```

Return a vector of size $n$ representing the number of implicit hydrogens connected to 1 to $n$th atoms of the given molecule.

"Implicit" means hydrogens are not represented as graph nodes, but it can be infered from the intrinsic valence of typical organic atoms.
