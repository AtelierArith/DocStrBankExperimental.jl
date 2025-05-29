```
WithoutReplacement(threshold=0.0) <: SpawningStrategy
```

[`SpawningStrategy`](@ref) where spawn targets are sampled without replacement. This strategy needs to allocate a temporary array during spawning, which makes it significantly less efficient than [`WithReplacement`](@ref).

If the number of spawn attempts is greater than the number of offdiagonals, this functions like [`Exact`](@ref), but is less efficient. For best performance, this strategy is to be used as a substrategy of [`DynamicSemistochastic`](@ref).

## Parameters

  * `threshold` sets the projection threshold. If set to zero, no projection is performed.

[`spawn!`](@ref) with this strategy returns the number of spawn attempts and the number of spawns.
