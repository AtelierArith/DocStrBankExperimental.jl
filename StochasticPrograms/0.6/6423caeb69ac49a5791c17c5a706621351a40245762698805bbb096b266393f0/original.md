```
evaluate_decision(stochasticprogram::TwoStageStochasticProgram, decision::AbstractVector)
```

Evaluate the first-stage `decision` in `stochasticprogram`.

In other words, evaluate the first-stage objective at `decision` and solve outcome models of `decision` for every available scenario. The supplied `decision` must match the defined decision variables in `stochasticprogram`. If a optimal solution to `stochasticprogram` has been determined, but [`cache_solution!`](@ref) has not been called, then the solution will be overwritten by this call. If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.
