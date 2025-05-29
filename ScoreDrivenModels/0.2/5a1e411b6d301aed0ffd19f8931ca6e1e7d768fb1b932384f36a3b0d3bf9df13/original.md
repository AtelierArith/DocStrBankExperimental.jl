```
simulate(series::Vector{T}, gas::ScoreDrivenModel{D, T}, H::Int, S::Int, kwargs...) where {D, T}
```

Generate scenarios for the future of a time series by updating the GAS recursion `H` times and taking a sample of the distribution until it generates `S` scenarios.

By default this method uses the `stationary_initial_params` method to perform the score driven recursion. If you estimated the model with a different set of `initial_params` use them here to maintain the coherence of your estimation.
