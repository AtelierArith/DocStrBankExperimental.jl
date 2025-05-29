```
alpha_dropout(rng::AbstractRNG, x, p, training)
alpha_dropout(rng::AbstractRNG, x, p, training, α, A, B)
```

Alpha Dropout: Dropout ensuring that the mean and variance of the output remains same as the input. For details see [klambauer2017self](@citet). Use the second call signature to avoid recomputing the constants for a fixed dropout probability.

## Arguments

  * `rng`: Random number generator
  * `x`: Input Array
  * `p`: Probability of an element to be dropped out
  * `training`: Set to `Val(true)` or `True()` if running in training mode. Can be set to `nothing` to automatically determine if the function is being called within an autodiff context`
  * `α`: `-1.7580993408473766`. Computed at limit x tends to infinity, `selu(x) = -λβ = α`
  * `A`: Scaling factor for the mean
  * `B`: Scaling factor for the variance

## Returns

  * Output Array after applying alpha dropout
  * Updated state for the random number generator
