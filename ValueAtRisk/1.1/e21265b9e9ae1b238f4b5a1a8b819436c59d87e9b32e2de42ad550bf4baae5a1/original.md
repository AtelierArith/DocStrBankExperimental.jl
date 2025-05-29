```
FilteredExtremeValueTheoryVaR{T} <: VaRModel{T}
```

A technique which fits an `ARCHModel` to the data and forecasts VaR by finding the quantile function of the innovation terms using Extreme Value Theory the standardized residuals. The VaR forecast combines the one-step ahead conditional mean estimate of the model and the result of the quantile function of the innovation terms scaled by the one-step ahead conditional volatility estimate
