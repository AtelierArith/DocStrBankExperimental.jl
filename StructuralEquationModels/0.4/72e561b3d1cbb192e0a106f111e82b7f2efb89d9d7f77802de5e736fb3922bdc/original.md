Subtype of `SemImplied` that implements the RAM notation with symbolic precomputation.

# Constructor

```
RAMSymbolic(;
    specification,
    vech = false,
    gradient = true,
    hessian = false,
    approximate_hessian = false,
    meanstructure = false,
    kwargs...)
```

# Arguments

  * `specification`: either a `RAMMatrices` or `ParameterTable` object
  * `meanstructure::Bool`: does the model have a meanstructure?
  * `gradient::Bool`: is gradient-based optimization used
  * `hessian::Bool`: is hessian-based optimization used
  * `approximate_hessian::Bool`: for hessian based optimization: should the hessian be approximated
  * `vech::Bool`: should the half-vectorization of Σ be computed (instead of the full matrix)   (automatically set to true if any of the loss functions is SemWLS)

# Extended help

## Interfaces

  * `param_labels(::RAMSymbolic)`-> vector of parameter ids
  * `nparams(::RAMSymbolic)` -> number of parameters
  * `ram.Σ` -> model implied covariance matrix
  * `ram.μ` -> model implied mean vector

Jacobians (only available in gradient! calls)

  * `ram.∇Σ` -> $∂vec(Σ)/∂θᵀ$
  * `ram.∇μ` -> $∂μ/∂θᵀ$
  * `ram.∇Σ_function` -> function to overwrite `∇Σ` in place,   i.e. `∇Σ_function(∇Σ, θ)`. Typically, you do not want to use this but simply   query `ram.∇Σ`.

Hessians The computation of hessians is more involved. Therefore, we desribe it in the online documentation,  and the respective interfaces are omitted here.

## RAM notation

The model implied covariance matrix is computed as

$$
    \Sigma = F(I-A)^{-1}S(I-A)^{-T}F^T
$$

and for models with a meanstructure, the model implied means are computed as

$$
    \mu = F(I-A)^{-1}M
$$
