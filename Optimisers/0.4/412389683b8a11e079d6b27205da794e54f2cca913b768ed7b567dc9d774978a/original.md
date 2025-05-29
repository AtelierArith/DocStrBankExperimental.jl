```
OAdam(η = 0.001, β = (0.5, 0.9), ϵ = 1e-8)
OAdam(; [eta, beta, epsilon])
```

[OAdam](https://arxiv.org/abs/1711.00141) (Optimistic Adam) is a variant of Adam adding an "optimistic" term suitable for adversarial training.

# Parameters

  * Learning rate (`η == eta`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple == beta`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * Machine epsilon (`ϵ == epsilon`): Constant to prevent division by zero                        (no need to change default)
