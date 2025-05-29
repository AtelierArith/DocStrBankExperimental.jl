```julia
struct FixedDofs{T} <: GradientRobustMultiPhysics.AbstractGlobalConstraint
```

fixes integral mean of the unknown to the specified value
