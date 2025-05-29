```
Bravais.DirectPoint{D} <: AbstractPoint{D}
```

A wrapper type over an `SVector{D, Float64}`, defining a single point in `D`-dimensional direct space. 

The coordinates of a Bravais.DirectPoint are generally assumed specified relative to an associated Bravais.DirectBasis. To convert to Cartesian coordinates, see [`cartesianize`](@ref).
