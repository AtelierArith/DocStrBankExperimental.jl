```
ccf(X, y; starting_lambdas = nothing)
```

Perform signed gradient descent for clipped convex functions for a given regression setting.

# Arguments

  * `X::AbstractMatrix{Float64}`: Design matrix of the linear model.
  * `y::AbstractVector{Float64}`: Response vector of the linear model.
  * `starting_lambdas::AbstractVector{Float64}`: Starting values of weighting parameters used by signed gradient descent.
  * `alpha::Float64`: Loss at which a point is labeled as an outlier. If unspecified, will be chosen as p*mean(residuals.^2), where residuals are OLS residuals.
  * `p::Float64`: Points that have squared OLS residual greater than p times the mean squared OLS residual are considered outliers.
  * `max_iter::Int64`: Maximum number of iterations to run signed gradient descent.
  * `beta::Float64`: Step size parameter.
  * `tol::Float64`: Tolerance below which convergence is declared.

# Output

  * `["betas"]`: Robust regression coefficients
  * `[""outliers"]`: Array of indices of outliers
  * `[""lambdas"]`: Lambda coefficients estimated in each iteration
  * `[""residuals"]`: Regression residuals.

# References

Barratt, S., Angeris, G. & Boyd, S. Minimizing a sum of clipped convex functions. Optim Lett 14, 2443–2459 (2020). https://doi.org/10.1007/s11590-020-01565-4
