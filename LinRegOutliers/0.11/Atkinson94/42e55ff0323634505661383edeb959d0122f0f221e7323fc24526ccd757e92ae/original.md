```
    atkinson94(setting, iters, crit)
```

Runs the Atkinson94 algorithm to find out outliers using LMS method.

# Arguments

  * `setting::RegressionSetting`: A regression setting object.
  * `iters::Int`: Number of random samples.
  * `crit::Float64`: Critical value for residuals

# Description

The algorithm randomly selects initial basic subsets and performs a very robust method, e.g `lms` to enlarge the basic subset. In each iteration of forward search, the best objective value and parameter  estimates are stored. These values are also used in Atkinson's Stalactite Plot for a visual investigation of  outliers. See `atkinsonstalactiteplot`.

# Output

  * `["optimum_index"]`: The iteration number in which the minimum objective is obtained
  * `["residuals_matrix"]`: Matrix of residuals obtained in each iteration
  * `["outliers"]`: Array of indices of detected outliers
  * `["objective"]`: Minimum objective value
  * `["coef"]`: Estimated regression coefficients
  * `["crit"]`: Critical value given by the user.

# Examples

```julia-repl
julia> reg = createRegressionSetting(@formula(stackloss ~ airflow + watertemp + acidcond), stackloss)
julia> atkinson94(reg)
Dict{Any,Any} with 6 entries:
  "optimum_index"    => 10
  "residuals_matrix" => [0.0286208 0.0620609 … 0.0796249 0.0; 0.0397778 0.120547 … 0.118437 0.0397778; … ; 1.21133 1.80846 … 0.690327 4.14366; 1.61977 0.971592 … 0.616204 3.58098]
  "outliers"         => [1, 3, 4, 21]
  "objective"        => 0.799134
  "coef"             => [-38.3133, 0.745659, 0.432794, 0.0104587]
  "crit"             => 3.0

```

# References

Atkinson, Anthony C. "Fast very robust methods for the detection of multiple outliers." Journal of the American Statistical Association 89.428 (1994): 1329-1339.
