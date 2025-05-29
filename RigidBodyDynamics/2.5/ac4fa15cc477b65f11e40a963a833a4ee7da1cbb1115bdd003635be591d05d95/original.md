```julia
mutable struct RigidBody{T}
```

A non-deformable body.

A `RigidBody` has inertia (represented as a [`SpatialInertia`](@ref)), unless it represents a root (world) body. A `RigidBody` additionally stores a list of definitions of coordinate systems that are rigidly attached to it.
