```julia
mutable struct Body{T} <: ConstrainedDynamics.AbstractBody{T}
```

A `Body` is a component of a [`Mechanism`](@ref).

# Important attributes

  * `id`:    The unique ID of a body. Assigned when added to a `Mechanism`.
  * `name`:  The name of a body. The name is taken from a URDF or can be assigned by the user.
  * `m`:     The mass of a body.
  * `J`:     The inertia of a body.
  * `state`: The state of a body. Contains all position and velocity information (see [`State`](@ref)).
  * `shape`: The visualization shape of a body (see [`Shape`](@ref)).

# Constructors

```
Body(m, J; name, shape)  
Mesh(path, m, J; scale, kwargs...)  
Box(x, y, z, m; kwargs...)  
Cylinder(r, h, m; kwargs...)  
Sphere(r, m; kwargs...)  
Pyramid(w, h, m; kwargs...)
```
