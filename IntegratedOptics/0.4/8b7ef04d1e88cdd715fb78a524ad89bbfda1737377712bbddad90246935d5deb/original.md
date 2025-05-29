```
ADAMW(η = 0.001, β::Tuple = (0.9, 0.999), decay = 0)
```

[ADAMW](https://arxiv.org/abs/1711.05101) is a variant of ADAM fixing (as in repairing) its weight decay regularization.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * `decay`: Decay applied to weights during optimisation.

# Examples

```julia
opt = ADAMW()
opt = ADAMW(0.001, (0.89, 0.995), 0.1)
```
