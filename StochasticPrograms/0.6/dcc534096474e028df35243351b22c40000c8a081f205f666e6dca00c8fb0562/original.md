```
EEV(stochasticprogram::TwoStageStochasticProgram)
```

Calculate the **expected value of the expected value solution** (`EEV`) of the two-stage `stochasticprogram`.

In other words, evaluate the `EVP` decision. If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`EVP`](@ref), [`EV`](@ref)
