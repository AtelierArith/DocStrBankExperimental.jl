```
EVP(stochasticprogram::TwoStageStochasticProgram; optimizer = nothing)
```

Generate the **expected value problem** (`EVP`) of the two-stage `stochasticprogram`.

In other words, generate a wait-and-see model corresponding to the expected scenario over all available scenarios in `stochasticprogram`. Optionally, a capable `optimizer` can be supplied to `WS`.

See also: [`expected_value_decision`](@ref), [`EEV`](@ref), [`EV`](@ref), [`WS`](@ref)
