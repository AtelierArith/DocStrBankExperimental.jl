```
AlphaDropout(p::Real)
```

AlphaDropout layer.

## Arguments

  * `p`: Probability of Dropout

      * if `p = 0` then [`NoOpLayer`](@ref) is returned.
      * if `p = 1` then `WrappedLayer(Base.Fix1(broadcast, zero))` is returned.

## Inputs

  * `x`: Must be an AbstractArray

## Returns

  * `x` with dropout mask applied if `training=Val(true)` else just `x`
  * State with updated `rng`

## States

  * `rng`: Pseudo Random Number Generator
  * `training`: Used to check if training/inference mode

Call [`Lux.testmode`](@ref) to switch to test mode.

See also [`Dropout`](@ref), [`VariationalHiddenDropout`](@ref)
