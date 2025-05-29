```
get_gradient(s::AbstractManoptSolverState)
```

return the (last stored) gradient within [`AbstractManoptSolverState`](@ref)``s`. By default also undecorates the state beforehand
