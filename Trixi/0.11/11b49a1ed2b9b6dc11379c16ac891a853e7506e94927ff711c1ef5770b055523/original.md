```
SemidiscretizationCoupled
```

A struct used to bundle multiple semidiscretizations. [`semidiscretize`](@ref) will return an `ODEProblem` that synchronizes time steps between the semidiscretizations. Each call of `rhs!` will call `rhs!` for each semidiscretization individually. The semidiscretizations can be coupled by gluing meshes together using [`BoundaryConditionCoupled`](@ref).

!!! warning "Experimental code"
    This is an experimental feature and can change any time.

