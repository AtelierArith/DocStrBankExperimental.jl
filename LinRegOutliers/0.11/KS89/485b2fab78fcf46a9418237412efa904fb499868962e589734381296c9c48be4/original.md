```
ks89(setting; alpha = 0.05)
```

Perform the Kianifard & Swallow (1989) algorithm for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `alpha::Float64`: Optional argument of the probability of rejecting the null hypothesis.

# Description

The algorithm starts with a clean subset of observations. This initial set is then enlarged  using recursive residuals. When the calculated statistics exceeds a threshold it terminates. 

# Output

  * `["outliers]`: Array of indices of outliers.
  * `["betas"]`: Vector of regression coefficients.

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(stackloss ~ airflow + watertemp + acidcond), stackloss)
julia> ks89(reg0001)
Dict{String, Vector} with 2 entries:
  "betas"    => [-42.4531, 0.956605, 0.555571, -0.108766]
  "outliers" => [4, 21]
```

# References

Kianifard, Farid, and William H. Swallow. "Using recursive residuals, calculated on adaptively-ordered observations, to identify outliers in linear regression." Biometrics (1989): 571-585.
