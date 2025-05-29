```
RandomWalkOptimizer
```

An optimizer that randomly pushes or pops operations. It doesn't optimize in any direction and is useful mainly for testing purposes.

This algorithm never reaches a fixpoint, so it does not implement [`optimize_to_fixpoint!`](@ref).
