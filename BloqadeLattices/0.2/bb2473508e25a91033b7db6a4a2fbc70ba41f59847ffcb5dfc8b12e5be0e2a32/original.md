```
AbstractLattice{D}
```

Supertype for all `D` dimensional lattices.

# Implementation

[`lattice_vectors`](@ref) and [`lattice_sites`](@ref) functions must be defined which should both return an indexable iterable containing the Bravais lattice vectors and  lattice sites respectively. (e.g.: [`GeneralLattice`](@ref) returns a tuple of tuples containing the  Bravais lattice vectors and lattice sites).
