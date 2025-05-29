```
EWS(stochasticprogram::StochasticProgram)
```

Calculate the **expected wait-and-see result** (`EWS`) of the `stochasticprogram`.

In other words, calculate the expectated result of all possible wait-and-see models, using the provided scenarios in `stochasticprogram`.

If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`VRP`](@ref), [`WS`](@ref)
