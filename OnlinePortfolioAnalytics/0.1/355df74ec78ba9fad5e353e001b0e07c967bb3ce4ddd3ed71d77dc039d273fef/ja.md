```julia
mutable struct AssetReturnMoments{T} <: OnlinePortfolioAnalytics.PortfolioAnalyticsMultiOutput{T}
```

```
AssetReturnMoments{T}()
```

`AssetReturnMoments`型は、4つの最初の統計的モーメント（`mean`、`std`、`skewness`、`kurtosis`）の計算を実装しています。
