```
get_stepsize(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, vars...)
```

return the stepsize stored within [`AbstractManoptSolverState`](@ref) `ams` when solving the [`AbstractManoptProblem`](@ref) `amp`. This method also works for decorated options and the [`Stepsize`](@ref) function within the options, by default stored in `ams.stepsize`.
