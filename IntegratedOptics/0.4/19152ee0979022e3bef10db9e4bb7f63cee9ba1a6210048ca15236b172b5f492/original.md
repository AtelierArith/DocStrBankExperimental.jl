```
RMSProp(η = 0.001, ρ = 0.9)
```

Optimizer using the [RMSProp](https://www.cs.toronto.edu/~tijmen/csc321/slides/lecture_slides_lec6.pdf) algorithm. Often a good choice for recurrent networks. Parameters other than learning rate generally don't need tuning.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Momentum (`ρ`): Controls the acceleration of gradient descent in the                 prominent direction, in effect dampening oscillations.

# Examples

```julia
opt = RMSProp()
opt = RMSProp(0.002, 0.95)
```
