```julia
mutable struct SimpleAssetReturn{T} <: OnlinePortfolioAnalytics.AssetReturn{T}
```

```
SimpleAssetReturn{T}(; period::Int = 1)
```

`SimpleAssetReturn`は資産リターン（単純法）計算を実装しています。

# パラメータ

  * `period`

# 使用法

## `SimpleAssetReturn`に1回の観測をフィードする

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
