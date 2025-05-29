```
AdamW(η = 1f-3, β = (9f-1, 9.99f-1), γ = 0, ϵ = eps(typeof(η)))
```

[AdamW](https://arxiv.org/abs/1711.05101) is a variant of Adam fixing (as in repairing) its weight decay regularization.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * Weight decay (`γ`): Decay applied to weights during optimisation.
  * Machine epsilon (`ϵ`): Constant to prevent division by zero                        (no need to change default)
