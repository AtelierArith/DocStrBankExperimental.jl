```
std(M, x, m=mean(M, x); corrected=true, kwargs...)
std(M, x, w::AbstractWeights, m=mean(M, x, w); corrected=false, kwargs...)
```

compute the optionally weighted standard deviation of a `Vector` `x` of `n` data points on the [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)  `M`, i.e.

$$
\sqrt{\frac{1}{c} \sum_{i=1}^n w_i d_{\mathcal M}^2 (x_i,m)},
$$

where `c` is a correction term, see [Statistics.std](https://juliastats.org/StatsBase.jl/stable/scalarstats/#Statistics.std). The mean of `x` can be specified as `m`, and the corrected variance can be activated by setting `corrected=true`.
