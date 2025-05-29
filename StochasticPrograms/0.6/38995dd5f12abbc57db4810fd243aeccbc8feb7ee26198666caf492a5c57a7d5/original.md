```
VSS(stochasticprogram::TwoStageStochasticProgram)
```

Calculate the **value of the stochastic solution** (`VSS`) of the two-stage `stochasticprogram`.

In other words, calculate the gap between `EEV` and `VRP`. If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.
