```julia
mutable struct StdDev{T} <: OnlinePortfolioAnalytics.PortfolioAnalyticsSingleOutput{T}
```

```
StdDev{T}()
```

`StdDev`型は標準偏差の計算を実装しています。
