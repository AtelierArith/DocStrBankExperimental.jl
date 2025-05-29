```julia
abstract type AbstractLattice{D, T, PB} <: LightLattices.AbstractNodeCollection{D, T}
```

The supertype for Lattices in `D`-dimensional space. Type `T` is used to represent coordinates. The boundary conditions can be either periodic (`PB=true`) or free (`PB=false`).
