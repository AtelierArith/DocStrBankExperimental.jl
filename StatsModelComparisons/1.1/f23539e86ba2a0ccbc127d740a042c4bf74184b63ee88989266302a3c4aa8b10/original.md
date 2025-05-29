```
gpdfitnew(x)
```

Estimate the paramaters for the Generalized Pareto Distribution (GPD). Returns empirical Bayes estimate for the parameters of the two-parameter generalized Parato distribution given the data.

# Arguments

  * `x::AbstractArray`: One dimensional data array.

# Returns

  * `k::Float64, sigma::Float64`: Estimated parameter values.

# Notes

  * This function returns a negative of Zhang and Stephens's k, because it is more common parameterization.
