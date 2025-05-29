```
expected_value_decision(stochasticprogram::TwoStageStochasticProgram)
```

Calculate the optimizer of the `EVP` of the two-stage `stochasticprogram`.

If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`EVP`](@ref), [`EV`](@ref), [`EEV`](@ref)
