```
wait_and_see_decision(stochasticprogram::TwoStageStochasticProgram, scenario::AbstractScenario, optimizer_constructor = nothing)
```

Calculate the optimizer of the **wait-and-see** (`WS`) model of the two-stage `stochasticprogram`, corresponding to `scenario`.

If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`WS`](@ref)
