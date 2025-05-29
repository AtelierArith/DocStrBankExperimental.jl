```julia
mutable struct SimpleAssetReturn{T} <: OnlinePortfolioAnalytics.AssetReturn{T}
```

```
SimpleAssetReturn{T}(; period::Int = 1)
```

The `SimpleAssetReturn` implements asset return (simple method) calculations.

# Parameters

  * `period`

# Usage

## Feed `SimpleAssetReturn` one observation at a time

```
julia> using OnlinePortfolioAnalytics

julia> ret = SimpleAssetReturn{Float64}()
SimpleAssetReturn: n=0 | value=missing

julia> fit!(ret, 10.0)
SimpleAssetReturn: n=1 | value=missing

julia> fit!(ret, 11.0)
SimpleAssetReturn: n=2 | value=0.1

julia> value(ret)
0.1
```
