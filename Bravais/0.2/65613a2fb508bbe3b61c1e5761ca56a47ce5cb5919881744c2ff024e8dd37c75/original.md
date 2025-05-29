```
Bravais.ReciprocalPoint{D} <: AbstractPoint{D}
```

A wrapper type over an `SVector{D, Float64}`, defining a single point in `D`-dimensional reciprocal space. 

The coordinates of a Bravais.ReciprocalPoint are generally assumed specified relative to an associated Bravais.ReciprocalBasis. To convert to Cartesian coordinates, see [`cartesianize`](@ref).
