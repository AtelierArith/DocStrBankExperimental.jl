```
var(M, x, m=mean(M, x); corrected=true)
var(M, x, w::AbstractWeights, m=mean(M, x, w); corrected=false)
```

compute the (optionally weighted) variance of a `Vector` `x` of `n` data points on the [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)  `M`, i.e.

$$
\frac{1}{c} \sum_{i=1}^n w_i d_{\mathcal M}^2 (x_i,m),
$$

where `c` is a correction term, see [Statistics.var](https://juliastats.org/StatsBase.jl/stable/scalarstats/#Statistics.var). The mean of `x` can be specified as `m`, and the corrected variance can be activated by setting `corrected=true`. All further `kwargs...` are passed to the computation of the mean (if that is not provided).
