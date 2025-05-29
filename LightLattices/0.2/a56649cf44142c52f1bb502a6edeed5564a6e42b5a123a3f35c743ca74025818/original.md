```julia
struct TrivialCell{D, T} <: LightLattices.AbstractCell{D, T}
```

Trivial cell consisting of one node at the origin of `D`-dimensional coordinate system. The type `T` is used to represent coordinates.
