```
cocoForwardSim(n, x_prev, type, order, parameter, covariates=nothing, link="log", add_help=order * -1 + 2, x=zeros(Int(n + length(x_prev) + add_help)))
```

Simulates forward count data for `n` steps given previous counts, model parameters, and optional covariates.

# Arguments

  * `n`: The number of future steps to simulate.
  * `x_prev`: A vector of previous count values used for initializing the simulation.
  * `type`: A string indicating the model type (e.g., `"GP"` for generalized Poisson).
  * `order`: The autoregressive model order (1 or 2).
  * `parameter`: A vector of model parameters.
  * `covariates` (optional): A matrix of covariate data used in simulation.
  * `link` (optional): A string specifying the link function to use (default is `"log"`).
  * `add_help` (optional): A helper parameter for simulation (default computed as `order * -1 + 2`).
  * `x` (optional): A preallocated vector of integer counts with length `n + length(x_prev) + add_help`.

# Returns

A vector of simulated counts for the `n` forward steps.
