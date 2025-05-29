```
NADAM(η = 0.001, β::Tuple = (0.9, 0.999))
```

[NADAM](https://openreview.net/forum?id=OM0jvwB8jIp57ZJjtNEZ) is a Nesterov variant of ADAM. Parameters don't need tuning.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.

# Examples

```julia
opt = NADAM()
opt = NADAM(0.002, (0.89, 0.995))
```
