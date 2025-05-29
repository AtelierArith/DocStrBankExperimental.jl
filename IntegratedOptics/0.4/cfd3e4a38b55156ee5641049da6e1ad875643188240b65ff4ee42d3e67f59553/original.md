```
ADAM(η = 0.001, β::Tuple = (0.9, 0.999))
```

[ADAM](https://arxiv.org/abs/1412.6980) optimiser.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.

# Examples

```julia
opt = ADAM()
opt = ADAM(0.001, (0.9, 0.8))
```
