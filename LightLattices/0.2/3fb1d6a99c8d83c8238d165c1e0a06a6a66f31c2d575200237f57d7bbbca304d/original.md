```julia
abstract type AbstractCell{D, T} <: LightLattices.AbstractNodeCollection{D, T}
```

Abstract unordered collection of nodes in `D`-dimensional space. Type `T` is used to represent coordinates.
