```
IsDynamicSemistochastic{T=Float64}(; kwargs...) <: StochasticStyle{T}
```

QMC propagation with floating-point walker numbers and reduced noise. All possible spawns (offdiagonal elements in vector-matrix multiplication) are performed deterministically when number of walkers in a configuration is high, as controlled by the `rel_spawning_threshold` and `abs_spawning_threshold` keywords. Stochastic selection of spawns is controlled by the `spawning` keyword.

By default, a stochastic vector compression is applied after annihilations are completed. This behaviour can be changed to on-the-fly projection (as in [`IsStochasticInteger`](@ref) or [`IsStochasticWithThreshold`](@ref)) by setting `late_compression=false`, or modifying `spawning` and `compression`. See parameters below for a more detailed explanation.

## Parameters:

  * `threshold = 1.0`: Values below this number are stochastically projected to this value or zero. See also [`ThresholdCompression`](@ref).
  * `late_compression = true`: If this is set to `true`, stochastic vector compression is performed after all the spawns are performed. If it is set to `false`, values are stochastically projected as they are being spawned. `late_compression=true` is equivalent to setting `compression=`[`ThresholdCompression`](@ref)`(threshold)` and `spawning=`[`WithReplacement`](@ref)`()`.  `late_compression=false` is equivalent to `compression=`[`NoCompression`](@ref)`()` and `spawning=WithReplacement(threshold)`.
  * `rel_spawning_threshold = 1.0`: If the walker number on a configuration times this threshold is greater than the number of offdiagonals, spawning is done deterministically. Should be set to 1 or more for best performance.
  * `abs_spawning_threshold = Inf`: If the walker number on a configuration is greater than this value, spawning is done deterministically. Can be set to e.g.  `abs_spawning_threshold = 0.1 * target_walkers`.
  * `spawning = WithReplacement()`: [`SpawningStrategy`](@ref) to use for the non-exact spawns.
  * `compression = ThresholdCompression(threshold)`: [`CompressionStrategy`](@ref) used to compress the vector after a step. Overrides `threshold`.

See also [`StochasticStyle`](@ref).
