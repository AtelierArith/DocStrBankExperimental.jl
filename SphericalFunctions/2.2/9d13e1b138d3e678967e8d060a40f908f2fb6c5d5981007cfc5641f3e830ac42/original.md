```
sYlm_prep(ℓₘₐₓ, sₘₐₓ, [T=Float64, [ℓₘᵢₙ=0]])
```

Construct storage space and pre-compute recursion coefficients to compute spin-weighted spherical-harmonic values ${}_{s}Y_{\ell, m}$ in place.

This returns the `sYlm_storage` arguments needed by [`sYlm_values!`](@ref).

Note that the result of this function can be passed to `sYlm_values!`, even if the value of `spin` passed to that function is smaller (in absolute value) than the `sₘₐₓ` passed to this function.  That is, the `sYlm_storage` returned by this function can be used to compute ${}_{s}Y_{\ell, m}$ values for numerous values of the spin.
