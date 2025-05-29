```
Dropout(p; dims=:)
```

Dropout layer.

## Arguments

  * `p`: Probability of Dropout (if `p = 0` then [`NoOpLayer`](@ref) is returned)

## Keyword Arguments

  * To apply dropout along certain dimension(s), specify the `dims` keyword. e.g. `Dropout(p; dims = (3,4))` will randomly zero out entire channels on WHCN input (also called 2D dropout).

## Inputs

  * `x`: Must be an AbstractArray

## Returns

  * `x` with dropout mask applied if `training=Val(true)` else just `x`
  * State with updated `rng`

## States

  * `rng`: Pseudo Random Number Generator
  * `training`: Used to check if training/inference mode

Call [`Lux.testmode`](@ref) to switch to test mode.

See also [`AlphaDropout`](@ref), [`VariationalHiddenDropout`](@ref)
