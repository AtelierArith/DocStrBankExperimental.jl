```julia
mutable struct LogAssetReturn{T} <: OnlinePortfolioAnalytics.AssetReturn{T}
```

```
LogAssetReturn{T}(; period::Int = 1)
```

The `LogAssetReturn` implements asset return (natural log method) calculations.

# Parameters

  * `period`

# Usage

## Feed `LogAssetReturn` one observation at a time

```
julia> using OnlinePortfolioAnalytics

julia> ret = LogAssetReturn{Float64}()
LogAssetReturn: n=0 | value=missing

julia> fit!(ret, 10.0)
LogAssetReturn: n=1 | value=missing

julia> fit!(ret, 11.0)
LogAssetReturn: n=2 | value=0.0953102

julia> value(ret)
0.09531017980432493
```
