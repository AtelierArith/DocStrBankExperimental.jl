```
critfunc(s, θ, rho; penalizediag=true)
```

Calculates the objective function value for the graphical lasso.

# Arguments

  * `s::AbstractMatrix`: Empirical covariance matrix.
  * `θ::AbstractMatrix`: Precision matrix.
  * `rho::Real`: Regularization parameter.
  * `penalizediag::Bool=true`: Whether to penalize the diagonal entries. (optional)

# Returns

  * `Real`: Value of the objective function.
