```julia
ExtraState{T,U} <: IterationState{T}
```

Extends `DefaultState` to track extra information each iteration. The field `other` can be of any type and is simply a storage facility for other data we want to preserve between iterations. It is not used to check convergence or in any other place inside IterationManagers.jl. It is simply a convenience for users who want to keep track of more than just explicit state on each iteration
