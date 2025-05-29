```julia
struct Rectangle{T} <: Euclid.AbstractGeometricPrimitive{T, 2}
```

  * `lower_corner::StaticArraysCore.SVector{3}`
  * `width::Any`
  * `height::Any`
