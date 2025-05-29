```
stop_solver!(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, i)
```

depending on the current [`AbstractManoptProblem`](@ref) `amp`, the current state of the solver stored in [`AbstractManoptSolverState`](@ref) `ams` and the current iterate `i` this function determines whether to stop the solver, which by default means to call the internal [`StoppingCriterion`](@ref). `ams.stop`
