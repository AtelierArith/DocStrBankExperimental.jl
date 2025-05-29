```
cocoSim(type, order, parameter, n, covariates=nothing, link="log", n_burn_in=200, x=zeros(Int(n + n_burn_in)))
```

Simulates a count time series based on an integer autoregressive model. The function accommodates both first-order and second-order models, with optional covariate information via a specified link function.

# Arguments

  * `type`: A string indicating the model type (e.g., `"GP"` for generalized Poisson). This parameter affects how the dispersion parameter `eta` is set.
  * `order`: An integer (1 or 2) specifying the autoregressive model order.
  * `parameter`: A vector of model parameters. For order 1 models, the first element is `alpha` and (if `type` is `"GP"`) the second is `eta`. For order 2 models, the first three elements are `alpha1`, `alpha2`, `alpha3`, and (if `type` is `"GP"`) the fourth is `eta`.
  * `n`: The number of observations to simulate after the burn-in period.
  * `covariates` (optional): A matrix of covariate values. If provided, these are used with the specified link function to compute the rate parameter `lambda`.
  * `link` (optional): A string specifying the link function to use (default is `"log"`).
  * `n_burn_in` (optional): The number of initial burn-in observations to discard (default is 200).
  * `x` (optional): An initial vector for the time series with length `n + n_burn_in`. Defaults to an integer array initialized with zeros.

# Returns

A vector of simulated count data of length `n`, corresponding to the time series after the burn-in period.

# Details

  * The rate parameter `lambda` is computed using a link function (obtained via `get_link_function(link)`) applied to the covariates if provided, or is set to the last element of `parameter` otherwise.
  * Depending on the model order, the appropriate autoregressive parameters are extracted from `parameter`.
  * For each time step (starting from t = 3), the simulated count is the sum of a draw from a custom autoregressive component (via `draw_random_g`) and a draw from a generalized Poisson component (via `draw_random_generalized_poisson_variable`).
