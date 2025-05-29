```
TransSubDIDResult{TR,P,M,I,TI} <: AbstractDIDResult{TR}
```

Estimation results obtained from a linear transformation of a subset of coefficient estimates from [`DIDResult`](@ref). See also [`TransformedDIDResult`](@ref), [`lincom`](@ref) and [`rescale`](@ref).

# Parameters

  * `P`: type of the result that is transformed.
  * `M`: type of the matrix representing the linear transformation.
  * `I`: type of indices for all coefficients.
  * `TI`: type of indices for treatment coefficients.
