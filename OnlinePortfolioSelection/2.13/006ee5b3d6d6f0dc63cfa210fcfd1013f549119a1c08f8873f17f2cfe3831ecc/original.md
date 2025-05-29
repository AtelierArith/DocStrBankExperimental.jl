```
PP<:TrendRep
```

Pick Price trend representation. Formula:

$$
{{\mathbf{\hat x}}_{M,t + 1}}\left( w \right) = \frac{{\mathop {\max }\limits_{0 \leqslant k \leqslant w - 1} {\mathbf{p}}_{t - k}^{(i)}}}{{{{\mathbf{p}}_t}}},\quad i = 1,2, \ldots ,d
$$

# Examples

```julia
julia> using OnlinePortfolioSelection

julia> pp = PP()
PP()
```
