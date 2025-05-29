```
dropout(rng::AbstractRNG, x, p, training, invp, dims)
dropout(rng::AbstractRNG, x, mask, p, training, update_mask::Union{Val, StaticBool},
    invp, dims)
```

Dropout: Simple Way to prevent Neural Networks for Overfitting. For details see [srivastava2014dropout](@citet).

## Arguments

  * `rng`: Random number generator
  * `x`: Input Array
  * `mask`: Dropout Mask. If not used then it is constructed automatically
  * `p`: Probability of an element to be dropped out
  * `training`: Set to `Val(true)` or `True()` if running in training mode. Can be set to `nothing` to automatically determine if the function is being called within an autodiff context
  * `update_mask`: If `Val(true)` or `True()` then the mask is generated and used. Else, the `mask` provided is directly used
  * `invp`: Inverse multiplied to the mask. Calculated as `invp = 1 / (1 - p)`.

## Returns

  * Output Array after applying dropout
  * Dropout Mask (if `training == false`, the returned value is meaningless)
  * Updated state for the random number generator
