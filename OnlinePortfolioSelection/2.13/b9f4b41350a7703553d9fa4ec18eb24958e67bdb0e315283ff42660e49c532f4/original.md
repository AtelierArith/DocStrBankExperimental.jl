SMAR<:TrendRep

Simple Moving Average trend representation **using the relative prices**. Formula:

$$
{\mathbf{1}} + \frac{{\mathbf{1}}}{{{{\mathbf{x}}_t}}} +  \cdots  + \frac{{\mathbf{1}}}{{ \otimes _{k = 0}^{w - 2}{{\mathbf{x}}_{t - k}}}}
$$

# Examples

```julia
julia> using OnlinePortfolioSelection

julia> sma = SMAR()
SMAR()
```
