```
recourse_decision(stochasticprogram::TwoStageStochasticProgram, decision::AbstractVector, scenario::AbstractScenario)
```

Determine the optimal recourse decision after taking the first-stage `decision` if `scenario` is the actual outcome in `stochasticprogram`. The supplied `decision` must match the defined decision variables in `stochasticprogram`. If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.
