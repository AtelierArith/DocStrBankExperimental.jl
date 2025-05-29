```
cocoReg(type, order, data, covariates=nothing, starting_values=nothing, link_function="log", lower_bound_covariates=-Inf, max_loop=nothing, optimizer=Fminbox(LBFGS()))
```

Fits a count regression model using either a generalized Poisson or Poisson likelihood based on the specified type and order. The function sets up the optimization problem, determines starting values and parameter bounds,  and minimizes the negative log-likelihood using an automatic differentiation optimizer.

# Arguments

  * `type`: A string indicating the model type ("GP" for generalized Poisson, "Poisson" for Poisson).
  * `order`: The autoregressive order (1 or 2).
  * `data`: A vector of observed counts.
  * `covariates` (optional): A matrix of covariate values.
  * `starting_values` (optional): Initial values for the optimizer.
  * `link_function` (optional): A string specifying the link function (default is `"log"`).
  * `lower_bound_covariates` (optional): Lower bound for covariate parameters (default is `-Inf`).
  * `max_loop` (optional): Parameter controlling the maximum iteration or truncation in likelihood computation.
  * `optimizer` (optional): The optimization algorithm to use (default is `Fminbox(LBFGS())`).

# Returns

A dictionary containing:

  * `"parameter"`: The fitted parameter vector.
  * `"covariance_matrix"`: The inverse Hessian matrix as an estimate of the parameter covariance.
  * `"log_likelihood"`: The log-likelihood value at the optimum.
  * Model details including `type`, `order`, `data`, `covariates`, `link`, starting values, optimizer settings, and parameter bounds.
  * `"se"`: The standard errors of the estimated parameters.
