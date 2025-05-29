```
AdaMax(η = 0.001, β::Tuple = (0.9, 0.999))
```

[AdaMax](https://arxiv.org/abs/1412.6980) is a variant of ADAM based on the ∞-norm.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.

# Examples

```julia
opt = AdaMax()
opt = AdaMax(0.001, (0.9, 0.995))
```
