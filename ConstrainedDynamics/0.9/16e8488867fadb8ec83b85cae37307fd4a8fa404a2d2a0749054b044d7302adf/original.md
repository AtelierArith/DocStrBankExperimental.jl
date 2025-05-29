```julia
mutable struct Mesh{T} <: ConstrainedDynamics.Shape{T}
```

A `Mesh` can be used to visualize arbitrary geometries.

# Important attributes

  * `path`: The path to the geometry file.
