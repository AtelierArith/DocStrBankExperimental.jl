```
Heatmap(xedges, yedges; left = true, closed = true)
Heatmap(itr; left = true, closed = true)
```

Create a two dimensional histogram with the bin partition created by `xedges` and `yedges`. When fitting a new observation, the first value will be associated with X, the second with Y.

  * If `left`, the bins will be left-closed.
  * If `closed`, the bins on the ends will be closed.  See [`Hist`](@ref).

# Example

```
using Plots

xy = zip(randn(10^6), randn(10^6))
o = fit!(HeatMap(-5:.1:5, -5:.1:5), xy)
plot(o)

xy = zip(1 .+ randn(10^6) ./ 10, randn(10^6))
o = HeatMap(xy)
plot(o, marginals=false)
plot(o)
```
