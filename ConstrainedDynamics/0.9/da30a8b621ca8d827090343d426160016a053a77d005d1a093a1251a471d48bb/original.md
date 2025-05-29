```julia
mutable struct Pyramid{T} <: ConstrainedDynamics.Shape{T}
```

A square `Pyramid` with a base in the x-y-plane.

  * `wh`: The pyramid width and height (vector).
