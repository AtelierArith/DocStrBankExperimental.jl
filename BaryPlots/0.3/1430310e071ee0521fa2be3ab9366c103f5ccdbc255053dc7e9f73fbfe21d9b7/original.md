```
check_stability(x_eq::Vector{Float64}, params::ReplicatorParams; stability_tol::Float64 = 1e-6) -> Bool
```

Determines the stability of an equilibrium point by analyzing the eigenvalues of the Jacobian matrix of the reduced system.

# Arguments

  * `x_eq`: A vector representing the strategy frequencies at the equilibrium point.
  * `params`: A `ReplicatorParams` struct containing the payoff functions and extra parameters.
  * `stability_tol`: Tolerance for determining the stability based on eigenvalues.

# Returns

  * `true` if the equilibrium is stable, `false` otherwise.

# Notes

  * The reduced system excludes one variable due to the simplex constraint (sum to 1).
  * Stability is determined by the sign of the real parts of the eigenvalues.
