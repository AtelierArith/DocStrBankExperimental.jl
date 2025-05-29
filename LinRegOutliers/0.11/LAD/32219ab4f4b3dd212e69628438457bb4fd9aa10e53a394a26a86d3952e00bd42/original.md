```
lad(setting; exact = true)
```

Perform Least Absolute Deviations regression for a given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `exact::Bool`: If true, use exact LAD regression. If false, estimate LAD regression parameters using GA. Default is true.

# Description

The LAD estimator searches for regression the parameters estimates that minimize the sum of absolute residuals. The optimization problem is 

Min z = u1(-) + u1(+) + u2(-) + u2(+) + .... + un(-) + un(+) Subject to:     y*1 - beta0 - beta1 * x*2 + u1(-) - u1(+) = 0     y*2 - beta0 - beta1 * x*2 + u2(-) - u2(+) = 0     .     .     .     y*n - beta0 - beta1 * x*n + un(-) - un(+) = 0 where      ui(-), ui(+) >= 0     i = 1, 2, ..., n      beta0, beta1 in R      n : Number of observations 

# Output

  * `["betas"]`: Estimated regression coefficients
  * `["residuals"]`: Regression residuals
  * `["model"]`: Linear Programming Model

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> lad(reg0001)
Dict{Any,Any} with 2 entries:
  "betas"     => [-57.3269, 1.19155]
  "residuals" => [2.14958, 1.25803, 0.0664872, 0.0749413, -0.416605, -0.90815, -1.2997, -1.79124,…

```
