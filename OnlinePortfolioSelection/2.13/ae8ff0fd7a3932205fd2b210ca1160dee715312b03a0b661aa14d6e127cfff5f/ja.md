```
EMA{T<:AbstractFloat}<:TrendRep
```

指数移動平均トレンド表現。式：

$$
{{\mathbf{\hat x}}_{E,t + 1}}\left( \vartheta  \right) = \frac{{\sum\limits_{k = 0}^{t - 1} {{{\left( {1 - \vartheta } \right)}^k}} \vartheta {{\mathbf{p}}_{t - k}} + {{\left( {1 - \vartheta } \right)}^t}{{\mathbf{p}}_0}}}{{{{\mathbf{p}}_t}}}
$$

# フィールド

  * `v::T`: スムージングファクター。

# 例

```julia
julia> using OnlinePortfolioSelection

julia> ema = EMA(0.5)
EMA{Float64}(0.5)
```
