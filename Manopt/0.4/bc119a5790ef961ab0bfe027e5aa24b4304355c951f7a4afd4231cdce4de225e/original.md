```
update_stopping_criterion!(c::Stoppingcriterion, s::Symbol, v::value)
update_stopping_criterion!(s::AbstractManoptSolverState, symbol::Symbol, v::value)
update_stopping_criterion!(c::Stoppingcriterion, ::Val{Symbol}, v::value)
```

Update a value within a stopping criterion, specified by the symbol `s`, to `v`. If a criterion does not have a value assigned that corresponds to `s`, the update is ignored.

For the second signature, the stopping criterion within the [`AbstractManoptSolverState`](@ref) `o` is updated.

To see which symbol updates which value, see the specific stopping criteria. They should use dispatch per symbol value (the third signature).
