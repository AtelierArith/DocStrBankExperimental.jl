```julia
mutable struct Cylinder{T} <: ConstrainedDynamics.Shape{T}
```

A `Cylinder` along the z-axis.

# Important attributes

  * `rh`: The cylinder radius and height (vector).
