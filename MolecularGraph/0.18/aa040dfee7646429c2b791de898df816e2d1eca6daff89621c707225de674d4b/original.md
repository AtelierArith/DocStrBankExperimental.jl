```
hybridization(mol::SimpleMolGraph) -> Vector{Int}
```

Returns a vector of size $n$ representing the orbital hybridization symbols (`:sp3`, `:sp2`, `:sp` or `:none`) of 1 to $n$th atoms of the given molecule.

The hybridization value in inorganic atoms and non-typical organic atoms will be `:none` (e.g. s, sp3d and sp3d2 orbitals). Note that this is a simplified geometry descriptor for substructure matching and does not reflect actual molecular orbital hybridization.
