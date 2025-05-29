```
FilteredHistoricalSimulationVaR{T} <: VaRModel{T}
```

A technique which fits an `ARCHModel` to the data and forecasts VaR by combining the one-step ahead conditional mean estimate of the model and the quantile of the empirical distributions of the standardized residuals of our data scaled by the one-step ahead conditional volatility estimate
