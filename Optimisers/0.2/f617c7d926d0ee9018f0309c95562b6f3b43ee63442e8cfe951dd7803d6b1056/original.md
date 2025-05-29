```
AdaMax(η = 1f-3, β = (9f-1, 9.99f-1), ϵ = eps(typeof(η)))
```

[AdaMax](https://arxiv.org/abs/1412.6980) is a variant of Adam based on the ∞-norm.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * Machine epsilon (`ϵ`): Constant to prevent division by zero                        (no need to change default)
