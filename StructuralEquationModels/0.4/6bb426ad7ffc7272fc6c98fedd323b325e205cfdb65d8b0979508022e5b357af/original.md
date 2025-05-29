Model implied covariance and means via RAM notation.

# Constructor

```
RAM(;specification,
    meanstructure = false,
    gradient = true,
    kwargs...)
```

# Arguments

  * `specification`: either a `RAMMatrices` or `ParameterTable` object
  * `meanstructure::Bool`: does the model have a meanstructure?
  * `gradient::Bool`: is gradient-based optimization used

# Extended help

## RAM notation

The model implied covariance matrix is computed as

$$
    \Sigma = F(I-A)^{-1}S(I-A)^{-T}F^T
$$

and for models with a meanstructure, the model implied means are computed as

$$
    \mu = F(I-A)^{-1}M
$$

## Interfaces

  * `param_labels(::RAM)`-> vector of parameter labels
  * `nparams(::RAM)` -> number of parameters
  * `ram.Σ` -> model implied covariance matrix
  * `ram.μ` -> model implied mean vector

RAM matrices for the current parameter values:

  * `ram.A`
  * `ram.S`
  * `ram.F`
  * `ram.M`

Jacobians of RAM matrices w.r.t to the parameter vector `θ`

  * `ram.∇A` -> $∂vec(A)/∂θᵀ$
  * `ram.∇S` -> $∂vec(S)/∂θᵀ$
  * `ram.∇M` = $∂M/∂θᵀ$

Vector of indices of each parameter in the respective RAM matrix:

  * `ram.A_indices`
  * `ram.S_indices`
  * `ram.M_indices`

Additional interfaces

  * `ram.F⨉I_A⁻¹` -> $F(I-A)^{-1}$
  * `ram.F⨉I_A⁻¹S` -> $F(I-A)^{-1}S$
  * `ram.I_A` -> $I-A$

Only available in gradient! calls:

  * `ram.I_A⁻¹` -> $(I-A)^{-1}$
