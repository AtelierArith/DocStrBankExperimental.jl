```
valence(mol::SimpleMolGraph) -> Vector{Int}
```

Return a vector of size $n$ representing the intrinsic valence of 1 to $n$th atoms of the given molecule.

The number of implicit hydrogens would be calculated based on the valence. The valence of a hypervalent atom or a non-organic atom is the same as its `apparent_valence`. This property corresponds to SMARTS `v` query.
