```
find_equilibria(
    payoff_functions::Tuple{Function, Function, Function},
    params::NamedTuple;
    num_initial_guesses::Int = 1000,
    solver_tol::Float64 = 1e-8,
    equilibrium_tol::Float64 = 1e-5,
    validity_tol::Float64 = 1e-6,
    stability_tol::Float64 = 1e-6
) -> Tuple{Vector{Vector{Float64}}, Vector{Bool}}
```

Finds the equilibria of the replicator dynamics system by numerically solving for points where the strategy frequencies stop changing.

# Arguments

  * `payoff_functions`: A tuple of three payoff functions corresponding to each strategy.
  * `params`: Extra parameters for the payoff functions (optional).
  * `num_initial_guesses`: Number of initial guesses to use for finding equilibria.
  * `solver_tol`: Tolerance for the numerical solver.
  * `equilibrium_tol`: Tolerance for considering equilibria as unique.
  * `validity_tol`: Tolerance for validating equilibria within the simplex.
  * `stability_tol`: Tolerance for stability analysis.

# Returns

  * A tuple containing:

      * `equilibria`: A vector of strategy frequencies representing the equilibria.
      * `stability_status`: A vector of booleans indicating whether each equilibrium is stable.

# Notes

  * Uses `nlsolve` to find roots of the replicator equation.
  * Filters out equilibria that are outside the simplex or are duplicates.
