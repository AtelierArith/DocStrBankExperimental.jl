```julia
struct CombineDofs{T} <: GradientRobustMultiPhysics.AbstractGlobalConstraint
```

combines specified degrees of freedom of two unknown (can be the same), which allows to glue together different unknowns in different regions or periodic boundary conditions
