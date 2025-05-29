```julia
mutable struct AssetReturnMoments{T} <: OnlinePortfolioAnalytics.PortfolioAnalyticsMultiOutput{T}
```

```
AssetReturnMoments{T}()
```

The `AssetReturnMoments` type implements 4 first statistical moments (`mean`, `std`, `skewness`, `kurtosis`) calculations.
