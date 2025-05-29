```julia
mutable struct Origin{T} <: ConstrainedDynamics.AbstractBody{T}
```

The `Origin` is the root of a [`Mechanism`](@ref).

# Important attributes

  * `id`:    The unique ID of the origin. Assigned when added to a `Mechanism`.
  * `name`:  The name of the origin. The name is taken from a URDF or can be assigned by the user.
  * `shape`: The visualization shape of the origin (see [`Shape`](@ref)).

# Constructors

```
Origin(; name, shape)  
Origin{Type}(; name, shape)  
Origin(body)
```
