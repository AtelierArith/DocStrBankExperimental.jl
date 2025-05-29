```
WithReplacement(threshold=0.0) <: SpawningStrategy
```

[`SpawningStrategy`](@ref) where spawn targets are sampled with replacement. This is the default spawning strategy for most of the [`StochasticStyle`](@ref)s.

## Parameters

  * `threshold` sets the projection threshold. If set to zero, no projection is performed.

[`spawn!`](@ref) with this strategy returns the number of spawn attempts and the number of spawns.
