```
OADAM(η = 0.0001, β::Tuple = (0.5, 0.9))
```

[OADAM](https://arxiv.org/abs/1711.00141) (Optimistic ADAM) is a variant of ADAM adding an "optimistic" term suitable for adversarial training.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.

# Examples

```julia
opt = OADAM()
opt = OADAM(0.001, (0.9, 0.995))
```
