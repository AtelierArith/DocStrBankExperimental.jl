```
multiplicity(mol::MolGraph) -> Vector{Int}
```

Return a vector of size $n$ representing atom multiplicities of 1 to $n$th atoms of the given molecule (1: non-radical, 2: radical, 3: biradical).
