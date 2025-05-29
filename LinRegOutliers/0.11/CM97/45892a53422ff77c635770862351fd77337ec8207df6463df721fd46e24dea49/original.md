```
cm97(setting; maxiter = 1000)
```

Perform the Chatterjee and Mächler (1997) algorithm for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.

# Description

The algorithm performs a iteratively weighted least squares estimation to obtain robust regression coefficients.

# Output

  * `["betas"]`: Robust regression coefficients
  * `["iterations"]`: Number of iterations performed
  * `["converged"]`: true if the algorithm converges, otherwise, false.

# Examples

```julia-repl
julia> myreg = createRegressionSetting(@formula(stackloss ~ airflow + watertemp + acidcond), stackloss)
julia> result = cm97(myreg)
Dict{String,Any} with 3 entries:
  "betas"      => [-37.0007, 0.839285, 0.632333, -0.113208]
  "iterations" => 22
  "converged"  => true
```

# References

Chatterjee, Samprit, and Martin Mächler. "Robust regression: A weighted least squares approach."  Communications in Statistics-Theory and Methods 26.6 (1997): 1381-1394.
