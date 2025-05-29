```
VariationalHiddenDropout(p; dims=:)
```

VariationalHiddenDropout layer. The only difference from Dropout is that the `mask` is retained until [`Lux.update_state(l, :update_mask, Val(true))`](@ref) is called.

## Arguments

  * `p`: Probability of Dropout (if `p = 0` then [`NoOpLayer`](@ref) is returned)

## Keyword Arguments

  * To apply dropout along certain dimension(s), specify the `dims` keyword. e.g. `VariationalHiddenDropout(p; dims = 3)` will randomly zero out entire channels on WHCN input (also called 2D dropout).

## Inputs

  * `x`: Must be an AbstractArray

## Returns

  * `x` with dropout mask applied if `training=Val(true)` else just `x`
  * State with updated `rng`

## States

  * `rng`: Pseudo Random Number Generator
  * `training`: Used to check if training/inference mode
  * `mask`: Dropout mask. Initilly set to nothing. After every run, contains the mask applied in that call
  * `update_mask`: Stores whether new mask needs to be generated in the current call

Call [`Lux.testmode`](@ref) to switch to test mode.

See also [`AlphaDropout`](@ref), [`Dropout`](@ref)
