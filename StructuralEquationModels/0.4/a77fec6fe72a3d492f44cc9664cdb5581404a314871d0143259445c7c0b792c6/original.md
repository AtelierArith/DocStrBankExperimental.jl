Weighted least squares estimation. At the moment only available with the `RAMSymbolic` implied type.

# Constructor

```
SemWLS(;
    observed,
    meanstructure = false,
    wls_weight_matrix = nothing,
    wls_weight_matrix_mean = nothing,
    approximate_hessian = false,
    kwargs...)
```

# Arguments

  * `observed`: the `SemObserved` part of the model
  * `meanstructure::Bool`: does the model have a meanstructure?
  * `approximate_hessian::Bool`: should the hessian be swapped for an approximation
  * `wls_weight_matrix`: the weight matrix for weighted least squares.   Defaults to GLS estimation ($0.5*(D^T*kron(S,S)*D)$ where D is the duplication matrix   and S is the inverse of the observed covariance matrix)
  * `wls_weight_matrix_mean`: the weight matrix for the mean part of weighted least squares.   Defaults to GLS estimation (the inverse of the observed covariance matrix)

# Examples

```julia
my_wls = SemWLS(observed = my_observed)
```

# Interfaces

Analytic gradients are available, and for models without a meanstructure also analytic hessians.
