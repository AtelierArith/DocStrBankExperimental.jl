```
pi_electron(mol::SimpleMolGraph) -> Vector{Int}
```

Returns a vector of size $n$ representing the number of $\pi$ electrons of 1 to $n$th atoms of the given molecule.

The number of $\pi$ electrons is calculated as `valence` - `connectivity`. Typically, each atom connected to double bonds adds one pi electron for each, and each atom connected to a triple bond adds two pi electrons.
