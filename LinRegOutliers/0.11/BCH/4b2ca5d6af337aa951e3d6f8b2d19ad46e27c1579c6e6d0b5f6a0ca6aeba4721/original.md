```
bch(setting; alpha = 0.05, maxiter = 1000, epsilon = 0.000001)
```

Perform the Billor & Chatterjee & Hadi (2006) algorithm for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `alpha::Float64`: Optional argument of the probability of rejecting the null hypothesis.
  * `maxiter::Int`: Maximum number of iterations for calculating iterative weighted least squares estimates.
  * `epsilon::Float64`: Accuracy for determining convergency.

# Description

The algorithm initially constructs a basic subset. These basic subset is then used to  generate initial weights for a iteratively least squares estimation. Regression coefficients obtained  in this stage are robust regression estimates. Squared normalized distances and squared normalized  residuals are used in `bchplot` which serves a visual way for investigation of outliers and their  properties.

# Output

  * `["betas"]`: Final estimate of regression coefficients
  * `["squared.normalized.robust.distances"]`:
  * `["weights"]`: Final weights used in calculation of WLS estimates
  * `["outliers"]`: Array of indices of outliers
  * `["squared.normalized.residuals"]`: Array of squared normalized residuals
  * `["residuals"]`: Array of regression residuals
  * `["basic.subset"]`: Array of indices of basic subset.

# Examples

```julia-repl
julia> reg  = createRegressionSetting(@formula(calls ~ year), phones);
julia> Dict{Any,Any} with 7 entries:
"betas"                               => [-55.9205, 1.15572]
"squared.normalized.robust.distances" => [0.104671, 0.0865052, 0.0700692, 0.0553633, 0.0423875, 0.03…
"weights"                             => [0.00186158, 0.00952088, 0.0787321, 0.0787321, 0.0787321, 0…
"outliers"                            => [1, 14, 15, 16, 17, 18, 19, 20, 21]
"squared.normalized.residuals"        => [5.53742e-5, 2.42977e-5, 2.36066e-6, 2.77706e-6, 1.07985e-7…
"residuals"                           => [2.5348, 1.67908, 0.523367, 0.567651, 0.111936, -0.343779, …
"basic.subset"                        => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10  …  15, 16, 17, 18, 19, 20, …
```

# References

Billor, Nedret, Samprit Chatterjee, and Ali S. Hadi. "A re-weighted least squares method  for robust regression estimation." American journal of mathematical and management sciences 26.3-4 (2006): 229-252.
