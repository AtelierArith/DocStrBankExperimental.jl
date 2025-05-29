```julia
mutable struct Box{T} <: ConstrainedDynamics.Shape{T}
```

A `Box`.

# Important attributes

  * `xyz`: The box size in x, y, and z direction (vector).
