SMAR<:TrendRep

単純移動平均トレンド表現 **相対価格を使用**。式：

$$
{\mathbf{1}} + \frac{{\mathbf{1}}}{{{{\mathbf{x}}_t}}} +  \cdots  + \frac{{\mathbf{1}}}{{ \otimes _{k = 0}^{w - 2}{{\mathbf{x}}_{t - k}}}}
$$

# 例

```julia
julia> using OnlinePortfolioSelection

julia> sma = SMAR()
SMAR()
```
