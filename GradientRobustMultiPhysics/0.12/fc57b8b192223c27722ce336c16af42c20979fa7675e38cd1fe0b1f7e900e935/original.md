```julia
abstract type IdentityDisc{DT<:GradientRobustMultiPhysics.DiscontinuityTreatment} <: id
```

identity jump operator: evaluates face jumps of finite element function
