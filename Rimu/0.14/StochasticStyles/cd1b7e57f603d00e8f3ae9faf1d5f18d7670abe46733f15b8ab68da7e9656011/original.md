```
DynamicSemistochastic(; strat, rel_threshold, abs_threshold) <: SpawningStrategy
```

[`SpawningStrategy`](@ref) that behaves like `strat` when the number of walkers is low, but performs exact steps when it is high. What "high" means is controlled by the two thresholds described below.

## Parameters

  * `strat = WithReplacement()`: a [`SpawningStrategy`](@ref) to use when the multiplication is not performed exactly. If the `strat` has a `threshold` different from zero, all spawns will be projected to that threshold.
  * `rel_threshold = 1.0`: When deciding on whether to perform an exact spawn, this value is multiplied to the number of walkers. Should be set to 1 or more for best performance. This threshold is affected by the `boost` argument to [`spawn!`](@ref).
  * `abs_threshold = Inf`: When deciding on whether to perform an exact spawn, `min(abs_threshold, num_offdiagonals)` is used. This threshold is not affected by the `boost` argument to [`spawn!`](@ref).

See e.g. [`WithoutReplacement`](@ref) for a description of the `strat.threshold` parameter.

[`spawn!`](@ref) with this strategy returns the numbers of exact and inexact spawns, the number of spawn attempts and the number of spawns.
