```julia
mutable struct CumulativeReturn{T} <: OnlinePortfolioAnalytics.PortfolioAnalyticsSingleOutput{T}
```

```
CumulativeReturn{T}()
```

`CumulativeReturn`型は累積リターン計算を実装しています。
