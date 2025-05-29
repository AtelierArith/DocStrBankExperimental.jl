```
VRP(stochasticprogram::StochasticProgram)
```

Calculate the **value of the recourse problem** (`VRP`) in `stochasticprogram`.

In other words, optimize the stochastic program and return the optimal value.

If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`EVPI`](@ref), [`EWS`](@ref)
