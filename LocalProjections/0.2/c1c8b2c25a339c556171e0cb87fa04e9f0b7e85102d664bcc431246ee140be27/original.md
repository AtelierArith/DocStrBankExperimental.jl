```
LeastSquaresLPResult{TF<:AbstractFloat} <: AbstractEstimatorResult
```

Additional results from estimating least squares local projections. See also [`LeastSquaresLP`](@ref) and [`LocalProjectionResult`](@ref).

# Field

  * `ms::Vector{OLS{TF}}`: data from the OLS regressions.
