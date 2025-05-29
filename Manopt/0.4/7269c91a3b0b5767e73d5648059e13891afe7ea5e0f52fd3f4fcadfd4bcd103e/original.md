```
StoppingCriterion
```

An abstract type for the functors representing stopping criteria, so they are callable structures. The naming Scheme follows functions, see for example [`StopAfterIteration`](@ref).

Every StoppingCriterion has to provide a constructor and its function has to have the interface `(p,o,i)` where a [`AbstractManoptProblem`](@ref) as well as [`AbstractManoptSolverState`](@ref) and the current number of iterations are the arguments and returns a boolean whether to stop or not.

By default each `StoppingCriterion` should provide a fields `reason` to provide details when a criterion is met (and that is empty otherwise).
