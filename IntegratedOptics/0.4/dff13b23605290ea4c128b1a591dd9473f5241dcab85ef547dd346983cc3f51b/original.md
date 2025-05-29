```
AMSGrad(η = 0.001, β::Tuple = (0.9, 0.999))
```

The [AMSGrad](https://openreview.net/forum?id=ryQu7f-RZ) version of the ADAM optimiser. Parameters don't need tuning.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.

# Examples

```julia
opt = AMSGrad()
opt = AMSGrad(0.001, (0.89, 0.995))
```
