```julia
mutable struct Sharpe{T} <: OnlinePortfolioAnalytics.PortfolioAnalyticsSingleOutput{T}
```

```
Sharpe{T}(; period=252, risk_free=0)
```

The `Sharpe` type implements sharpe ratio calculations.

# Parameters

  * `period`: default is `252`. Daily (`252`), Hourly (`252*6.5`), Minutely(`252*6.5*60`) etc...
  * `risk_free`: default is `0`. Constant risk-free return throughout the period.
