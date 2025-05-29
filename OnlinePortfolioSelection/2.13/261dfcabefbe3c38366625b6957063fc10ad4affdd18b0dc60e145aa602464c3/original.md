```
SMAP<:TrendRep
```

Simple Moving Average trend representation **using the close prices**. Formula:

$$
\mathbf{\hat{x}}_{S, t+1}\left(w\right)= \frac{\sum_{k=0}^{w-1}\mathbf{p}_{t-k}}{w\mathbf{p}_t}
$$

# Examples

```julia
julia> using OnlinePortfolioSelection

julia> sma = SMAP()
SMA()
```
