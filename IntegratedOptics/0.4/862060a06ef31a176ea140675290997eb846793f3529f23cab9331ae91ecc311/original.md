```
Momentum(η = 0.01, ρ = 0.9)
```

Gradient descent optimizer with learning rate `η` and momentum `ρ`.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Momentum (`ρ`): Controls the acceleration of gradient descent in the                 prominent direction, in effect dampening oscillations.

# Examples

```julia
opt = Momentum()
opt = Momentum(0.01, 0.99)
```
