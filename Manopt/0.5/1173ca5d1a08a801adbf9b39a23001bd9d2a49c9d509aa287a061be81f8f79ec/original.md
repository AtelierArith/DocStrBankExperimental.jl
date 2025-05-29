```
get_last_stepsize(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, vars...)
```

return the last computed stepsize stored within [`AbstractManoptSolverState`](@ref) `ams` when solving the [`AbstractManoptProblem`](@ref) `amp`.

This method takes into account that `ams` might be decorated. In case this returns `NaN`, a concrete call to the stored stepsize is performed. For this, usually, the first of the `vars...` should be the current iterate.
