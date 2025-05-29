```
RAdam(η = 0.001, β = (0.9, 0.999), ϵ = 1e-8)
RAdam(; [eta, beta, epsilon])
```

[Rectified Adam](https://arxiv.org/abs/1908.03265) optimizer.

# Parameters

  * Learning rate (`η == eta`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple == beta`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * Machine epsilon (`ϵ == epsilon`): Constant to prevent division by zero                        (no need to change default)
