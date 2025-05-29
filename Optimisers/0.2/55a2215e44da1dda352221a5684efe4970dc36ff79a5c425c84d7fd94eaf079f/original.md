```
Rprop(η = 1f-3, ℓ = (5f-1, 1.2f0), Γ = (1f-6, 50f0))
```

Optimizer using the [Rprop](https://ieeexplore.ieee.org/document/298623) algorithm. A full-batch learning algorithm that depends only on the sign of the gradient.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Scaling factors (`ℓ::Tuple`): Multiplicative increase and decrease factors.
  * Step sizes (`Γ::Tuple`): Mminimal and maximal allowed step sizes.
