```
DeepEquilibriumSolution(z_star, u₀, residual, jacobian_loss, nfe, solution)
```

Stores the solution of a DeepEquilibriumNetwork and its variants.

## Fields

  * `z_star`: Steady-State or the value reached due to maxiters
  * `u0`: Initial Condition
  * `residual`: Difference of the $z^*$ and $f(z^*, x)$
  * `jacobian_loss`: Jacobian Stabilization Loss (see individual networks to see how it can be computed)
  * `nfe`: Number of Function Evaluations
  * `original`: Original Internal Solution
