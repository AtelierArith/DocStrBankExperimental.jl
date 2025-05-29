```
mdop_maximum_delay(s, tw = 1:50, samplesize = 1.0)) -> τ_max, L
```

Compute an upper bound for the search of optimal delays, when using `mdop_embedding` [`mdop_embedding`](@ref) or `beta_statistic` [`beta_statistic`](@ref).

## Description

The input time series `s` gets embedded with unit lag and increasing dimension, for dimensions (or time windows) `tw` (`RangeObject`). For each of such a time window the `L`-statistic from Uzal et al. [^Uzal2011] will be computed. `samplesize` determines the fraction of points to be considered in the computation of `L` (see [`uzal_cost`](@ref)). When this statistic reaches its global minimum the maximum delay value `τ_max` gets returned. When `s` is a multivariate `Dataset`, `τ_max` will becomputed for all timeseries of that Dataset and the maximum value will be returned. The returned `L`-statistic has size `(length(tw), size(s,2))`.

[^Nichkawde2013]: Nichkawde, Chetan (2013). [Optimal state-space reconstruction using derivatives on projected manifold. Physical Review E 87, 022905](https://doi.org/10.1103/PhysRevE.87.022905).

[^Uzal2011]: Uzal, L. C., Grinblat, G. L., Verdes, P. F. (2011). [Optimal reconstruction of dynamical systems: A noise amplification approach. Physical Review E 84, 016223](https://doi.org/10.1103/PhysRevE.84.016223).
