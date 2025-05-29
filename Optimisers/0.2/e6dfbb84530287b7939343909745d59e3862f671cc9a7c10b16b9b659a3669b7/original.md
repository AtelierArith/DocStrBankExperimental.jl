```
OAdam(η = 1f-3, β = (5f-1, 9f-1), ϵ = eps(typeof(η)))
```

[OAdam](https://arxiv.org/abs/1711.00141) (Optimistic Adam) is a variant of Adam adding an "optimistic" term suitable for adversarial training.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * Machine epsilon (`ϵ`): Constant to prevent division by zero                        (no need to change default)
