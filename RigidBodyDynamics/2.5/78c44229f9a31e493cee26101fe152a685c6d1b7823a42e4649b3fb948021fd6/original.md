```julia
struct WrenchesCache{M} <: RigidBodyDynamics.AbstractTypeDict
```

A container that manages the creation and storage of `BodyDict{Wrench{T}}`. Similar to [`StateCache`](@ref).
