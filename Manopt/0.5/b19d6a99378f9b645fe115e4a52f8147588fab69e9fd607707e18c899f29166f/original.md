```
get_stopping_criterion(ams::AbstractManoptSolverState)
```

Return the [`StoppingCriterion`](@ref) stored within the [`AbstractManoptSolverState`](@ref) `ams`.

For an undecorated state, this is assumed to be in `ams.stop`. Overwrite `_get_stopping_criterion(yms::YMS)` to change this for your manopt solver (`yms`) assuming it has type YMS`.
