```
estimate_objective([rng,] obj, q, prob; kwargs...)
```

Estimate the variational objective `obj` targeting `prob` with respect to the variational approximation `q`.

# Arguments

  * `rng::Random.AbstractRNG`: Random number generator.
  * `obj::AbstractVariationalObjective`: Variational objective.
  * `prob`: The target log-joint likelihood implementing the `LogDensityProblem` interface.
  * `q`: Variational approximation.

# Keyword Arguments

Depending on the objective, additional keyword arguments may apply. Please refer to the respective documentation of each variational objective for more info.

# Returns

  * `obj_est`: Estimate of the objective value.
