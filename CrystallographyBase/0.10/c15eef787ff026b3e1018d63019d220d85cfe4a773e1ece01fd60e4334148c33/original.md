```
Cell(lattice, positions, atoms)
```

Create a new cell.

Argument `lattice` is a [`Lattice`](@ref) type. Fractional atomic positions `positions` are given by a vector of $N$ vectors with floating point values, where $N$ is the number of atoms. Argument `atoms` is a list of $N$ values, where the same kind of atoms need to be the same type.
