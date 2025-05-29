```
RADAM(η = 0.001, β::Tuple = (0.9, 0.999))
```

[Rectified ADAM](https://arxiv.org/abs/1908.03265) optimizer.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.

# Examples

```julia
opt = RADAM()
opt = RADAM(0.001, (0.9, 0.8))
```
