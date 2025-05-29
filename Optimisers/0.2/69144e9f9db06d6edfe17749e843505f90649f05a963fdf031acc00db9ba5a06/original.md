```
AdaBelief(η = 1f-3, β = (9f-1, 9.99f-1), ϵ = 1e-16)
```

The [AdaBelief](https://arxiv.org/abs/2010.07468) optimiser is a variant of the well-known Adam optimiser.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * Machine epsilon (`ϵ::Float32`): Constant to prevent division by zero                                 (no need to change default)
