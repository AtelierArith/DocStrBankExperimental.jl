```
Rprop(η = 1e-3, ℓ = (0.5, 1.2), Γ = (1e-6, 50.0))
Rprop(; [eta, ell, gamma])
```

Optimizer using the [Rprop](https://ieeexplore.ieee.org/document/298623) algorithm. A full-batch learning algorithm that depends only on the sign of the gradient.

# Parameters

  * Learning rate (`η == eta`): Amount by which gradients are discounted before updating                      the weights.
  * Scaling factors (`ℓ::Tuple == ell`): Multiplicative increase and decrease factors.
  * Step sizes (`Γ::Tuple == gamma`): Mminimal and maximal allowed step sizes.
