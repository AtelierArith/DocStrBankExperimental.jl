```
calculate_coeffs(result::Union{BFGSResult, CompositeBFGSResult}
                 logAge::AbstractVector{<:Number},
                 metallicities::AbstractVector{<:Number})
```

Returns per-SSP stellar mass coefficients ($r_{j,k}$ in the [derivation](@ref mzr_derivation)) using the optimized metallicity model, metallicity dispersion model, and stellar mass coefficients from the result of a BFGS optimization. In the case that the provided `result` is a `CompositeBFGSResult` containing both the maximum a posteriori and maximum likelihood estimate (MLE), the MLE is used to construct the coefficients.
