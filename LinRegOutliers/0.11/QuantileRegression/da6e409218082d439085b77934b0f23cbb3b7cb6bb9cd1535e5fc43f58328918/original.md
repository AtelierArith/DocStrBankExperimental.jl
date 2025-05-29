```
quantileregression(setting; tau = 0.5)
```

Perform Quantile Regression for a given regression setting (multiple linear regression).

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `tau::Float64`: Quantile level. Default is 0.5.

# Description

The Quantile Regression estimator searches for the regression parameter estimates that minimize the 

Min z = (1 - tau) (u1(-) + u2(-) + ... + un(-)) + tau (u1(+) + u2(+) + ... + un(+)) Subject to:     y*1 - beta0 - beta1 * x*2 + u1(-) - u1(+) = 0     y*2 - beta0 - beta1 * x*2 + u2(-) - u2(+) = 0     .     .     .     y*n - beta0 - beta1 * x*n + un(-) - un(+) = 0 where      ui(-), ui(+) >= 0     i = 1, 2, ..., n      beta0, beta1 in R      n : Number of observations      model is the y = beta1 + beta2 * x + u 

# Output

  * `["betas"]`: Estimated regression coefficients
  * `["residuals"]`: Regression residuals
  * `["model"]`: Linear Programming Model

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> quantileregression(reg0001)
```
