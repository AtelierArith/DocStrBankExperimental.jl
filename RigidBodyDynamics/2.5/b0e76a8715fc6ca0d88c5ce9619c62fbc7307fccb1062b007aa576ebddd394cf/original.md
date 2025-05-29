```julia
struct SegmentedVectorCache{K, KeyRange<:AbstractUnitRange{K}} <: RigidBodyDynamics.AbstractTypeDict
```

A container that manages the creation and storage of heterogeneously typed [`SegmentedVector`](@ref) objects. Similar to [`StateCache`](@ref).
