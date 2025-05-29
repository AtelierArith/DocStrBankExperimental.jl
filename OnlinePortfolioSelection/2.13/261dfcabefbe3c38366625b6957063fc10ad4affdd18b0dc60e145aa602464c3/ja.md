```
SMAP<:TrendRep
```

単純移動平均トレンド表現 **終値を使用して**。式：

$$
\mathbf{\hat{x}}_{S, t+1}\left(w\right)= \frac{\sum_{k=0}^{w-1}\mathbf{p}_{t-k}}{w\mathbf{p}_t}
$$

# 例

```julia
julia> using OnlinePortfolioSelection

julia> sma = SMAP()
SMA()
```
