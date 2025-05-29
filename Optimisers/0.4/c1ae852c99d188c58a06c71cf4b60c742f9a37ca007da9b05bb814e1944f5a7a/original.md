```
Momentum(η = 0.01, ρ = 0.9)
Momentum(; [eta, rho])
```

Gradient descent optimizer with learning rate `η` and momentum `ρ`.

# Parameters

  * Learning rate (`η == eta`): Amount by which gradients are discounted before updating                      the weights.
  * Momentum (`ρ == rho`): Controls the acceleration of gradient descent in the                 prominent direction, in effect dampening oscillations.
