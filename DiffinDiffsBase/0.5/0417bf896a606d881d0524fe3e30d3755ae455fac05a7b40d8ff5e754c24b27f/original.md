```
SubDIDResult{TR,P<:AbstractDIDResult,I,TI} <: AbstractDIDResult{TR}
```

A view into a DID result of type `P` with indices for all coefficients of type `I` and indices for treatment coefficients of type `TI`. See also [`view(r::AbstractDIDResult, inds)`](@ref).
