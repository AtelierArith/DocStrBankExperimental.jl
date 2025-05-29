```
forecast(series::Vector{T}, gas::ScoreDrivenModel{D, T}, H::Int; kwargs...) where {D, T}
```

Forecast quantiles for future values of a time series by updating the GAS recursion `H` times and using Monte Carlo method as in Blasques, Francisco, Siem Jan Koopman, Katarzyna Lasak and Andre Lucas (2016): "In-Sample Confidence Bounds and Out-of-Sample Forecast Bands for Time-Varying Parameters in Observation Driven Models", International Journal of Forecasting, 32(3), 875-887.

You can pass the desired quantiles as a `Vector{T}`. The default behavior is to forecast the median and the `0.025` and `0.975` quantiles.

By default 1000 scenarios are used but you can change this by switching the `S` keyword argument.

By default this method uses the `stationary_initial_params` method to perform the score driven recursion. If you estimated the model with a different set of `initial_params` use them here to maintain the coherence of your estimation.
