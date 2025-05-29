```
get_iterate(O::AbstractManoptSolverState)
```

return the (last stored) iterate within [`AbstractManoptSolverState`](@ref)``s`. This should usually refer to a single point on the manifold the solver is working on

By default this also removes all decorators of the state beforehand.
