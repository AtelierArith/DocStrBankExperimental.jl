```
step_solver!(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, k)
```

Do one iteration step (the `i`th) for an [`AbstractManoptProblem`](@ref)`p` by modifying the values in the [`AbstractManoptSolverState`](@ref) `ams`.
