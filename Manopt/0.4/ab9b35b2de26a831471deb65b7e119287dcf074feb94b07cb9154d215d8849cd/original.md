```
AbstractManoptSolverState
```

A general super type for all solver states.

# Fields

The following fields are assumed to be default. If you use different ones, provide the access functions accordingly

  * `p` a point on a manifold with the current iterate
  * `stop` a [`StoppingCriterion`](@ref).
