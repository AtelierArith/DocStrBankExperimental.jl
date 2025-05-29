```
RAdam(η = 1f-3, β = (9f-1, 9.99f-1), ϵ = eps(typeof(η)))
```

[Rectified Adam](https://arxiv.org/abs/1908.03265) optimizer.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * Machine epsilon (`ϵ`): Constant to prevent division by zero                        (no need to change default)
