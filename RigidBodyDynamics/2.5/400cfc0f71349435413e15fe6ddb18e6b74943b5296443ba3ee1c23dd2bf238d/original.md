```julia
struct DynamicsResultCache{M} <: RigidBodyDynamics.AbstractTypeDict
```

A container that manages the creation and storage of [`DynamicsResult`](@ref) objects of various scalar types, associated with a given `Mechanism`. Similar to [`StateCache`](@ref).
