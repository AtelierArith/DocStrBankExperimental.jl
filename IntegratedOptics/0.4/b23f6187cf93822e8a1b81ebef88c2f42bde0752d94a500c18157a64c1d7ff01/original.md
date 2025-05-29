```
AdaBelief(η = 0.001, β::Tuple = (0.9, 0.999))
```

The [AdaBelief](https://arxiv.org/abs/2010.07468) optimiser is a variant of the well-known ADAM optimiser.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.

# Examples

```julia
opt = AdaBelief()
opt = AdaBelief(0.001, (0.9, 0.8))
```
