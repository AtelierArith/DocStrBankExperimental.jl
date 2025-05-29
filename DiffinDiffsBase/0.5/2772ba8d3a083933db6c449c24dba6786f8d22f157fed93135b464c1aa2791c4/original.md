```
TransformedDIDResult{TR,P,M} <: AbstractDIDResult{TR}
```

Estimation results obtained from a linear transformation of all coefficient estimates from [`DIDResult`](@ref). See also [`TransSubDIDResult`](@ref), [`lincom`](@ref) and [`rescale`](@ref).

# Parameters

  * `P`: type of the result that is transformed.
  * `M`: type of the matrix representing the linear transformation.
