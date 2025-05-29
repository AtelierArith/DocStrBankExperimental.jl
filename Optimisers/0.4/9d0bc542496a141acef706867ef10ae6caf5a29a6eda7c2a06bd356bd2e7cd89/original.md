```
Nesterov(η = 0.001, ρ = 0.9)
Nesterov(; [eta, rho])
```

Gradient descent optimizer with learning rate `η` and Nesterov momentum `ρ`.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Nesterov momentum (`ρ`): Controls the acceleration of gradient descent in the                          prominent direction, in effect dampening oscillations.
