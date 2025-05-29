```
AMSGrad(η = 1f-3, β = (9f-1, 9.99f-1), ϵ = eps(typeof(η)))
```

The [AMSGrad](https://openreview.net/forum?id=ryQu7f-RZ) version of the Adam optimiser. Parameters don't need tuning.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * Machine epsilon (`ϵ`): Constant to prevent division by zero                        (no need to change default)
