```
EVPI(stochasticprogram::TwoStageStochasticProgram)
```

Calculate the **expected value of perfect information** (`EVPI`) of the two-stage `stochasticprogram`.

In other words, calculate the gap between `VRP` and `EWS`. If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`VRP`](@ref), [`EWS`](@ref), [`VSS`](@ref)
