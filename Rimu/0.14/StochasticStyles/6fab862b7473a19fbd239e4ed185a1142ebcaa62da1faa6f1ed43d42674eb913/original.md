```
Bernoulli(threshold=0.0) <: SpawningStrategy
```

Perform Bernoulli sampling. A spawn is attempted on each offdiagonal element with a probability that results in an expected number of spawns equal to the number of walkers on the spawning configuration. This is significantly less efficient than [`WithReplacement`](@ref).

If the number of spawn attempts is greater than the number of offdiagonals, this functions like [`Exact`](@ref), but is less efficient. For best performance, this strategy is to be used as a substrategy of [`DynamicSemistochastic`](@ref).

## Parameters

  * `threshold` sets the projection threshold.

[`spawn!`](@ref) with this strategy returns the number of spawn attempts and the number of spawns.
