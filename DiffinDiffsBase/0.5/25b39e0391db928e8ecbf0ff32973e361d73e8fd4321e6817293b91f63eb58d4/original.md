```
rescale(r::AbstractDIDResult, scale::AbstractVector{<:Real}, subset=nothing)
rescale(r::AbstractDIDResult, by::Pair, subset=nothing)
```

Rescale the coefficient estimates from DID result `r`. The order of elements in `scale` must match the order of coefficients. If the length of `scale` is smaller than the total number of coefficient, `subset` must be specified with indices representing coefficients that remain after the transformation. Alternatively, if `by` is specified in the same way for [`apply`](@ref), the scales can be computed based on values in [`treatcells(r)`](@ref). In this case, only treatment coefficients are transformed even if `subset` is not specified. See [`lincom`](@ref) for more general transformation.
