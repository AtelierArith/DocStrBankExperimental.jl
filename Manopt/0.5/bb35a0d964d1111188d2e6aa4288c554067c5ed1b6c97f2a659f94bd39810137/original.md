```
get_reason(s::AbstractManoptSolverState)
```

return the current reason stored within the [`StoppingCriterion`](@ref) from within the [`AbstractManoptSolverState`](@ref). This reason is empty (`""`) if the criterion has never been met.
