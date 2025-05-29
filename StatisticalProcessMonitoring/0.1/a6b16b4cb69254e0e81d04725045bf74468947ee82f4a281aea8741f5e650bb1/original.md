```
LocationScaleStatistic{S, M, P}
```

A mutable struct representing a statistic applied to a location-scale family.

# Fields

  * `stat::S`: The statistic.
  * `μ::M`: The location parameter.
  * `Ω::P`: The inverse square root of the variance.

# Examples

```
STAT = EWMA(λ = 0.2)
RSTAT = LocationScaleStatistic(STAT, 1.0, 2.5)
```
