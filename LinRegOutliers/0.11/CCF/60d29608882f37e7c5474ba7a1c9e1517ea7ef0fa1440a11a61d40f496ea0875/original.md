```
ccf(setting; starting_lambdas = nothing)
```

Perform signed gradient descent for clipped convex functions for a given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `starting_lambdas::AbstractVector{Float64}`: Starting values of weighting parameters used by signed gradient descent.
  * `alpha::Float64`: Loss at which a point is labeled as an outlier (points with loss ≥ alpha will be called outliers).
  * `max_iter::Int64`: Maximum number of iterations to run signed gradient descent.
  * `beta::Float64`: Step size parameter.
  * `tol::Float64`: Tolerance below which convergence is declared.

# Output

  * `["betas"]`: Robust regression coefficients
  * `[""outliers"]`: Array of indices of outliers
  * `[""lambdas"]`: Lambda coefficients estimated in each iteration
  * `[""residuals"]`: Regression residuals.

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> ccf(reg0001)
Dict{Any,Any} with 4 entries:
  "betas"     => [-63.4816, 1.30406]
  "outliers"  => [15, 16, 17, 18, 19, 20]
  "lambdas"   => [1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0, 1.0  …  2.77556e-17, 2.77556e-17, 0…
  "residuals" => [-2.67878, -1.67473, -0.37067, -0.266613, 0.337444, 0.941501, 1.44556, 2.04962, 1…

```

# References

Barratt, S., Angeris, G. & Boyd, S. Minimizing a sum of clipped convex functions. Optim Lett 14, 2443–2459 (2020). https://doi.org/10.1007/s11590-020-01565-4
