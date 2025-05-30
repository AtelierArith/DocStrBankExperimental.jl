```
H!(H, expiβ, ℓₘₐₓ, m′ₘₐₓ, H_rec_coeffs)
H!(H, expiβ, ℓₘₐₓ, m′ₘₐₓ, H_rec_coeffs, Hindex)
```

Compute the $H$ matrix defined by [Gumerov_2015](@citet).

This computation forms the basis for computing Wigner's $d$ and $𝔇$ matrices via [`d_matrices!`](@ref) and [`D_matrices!`](@ref), the spin-weighted spherical harmonics via [`sYlm_values!`](@ref), and for transforming from values of spin-weighted spherical functions evaluated on a grid to the corresponding mode weights via [`map2salm`](@ref).

Due to symmetries, we only need to compute ~1/4 of the elements of this matrix, so only those elements with $m ≥ |m′|$ are computed.  The relevant indices of the `H` vector are computed based on the `Hindex` function — which defaults to `WignerHindex`, but could reasonably be `WignerDindex` if the input `H` vector contains all valid indices.  However, it is assumed that the storage scheme used for `H` is such that the successive $m$ values are located in successive elements.

If $m′ₘₐₓ < ℓₘₐₓ$, we don't even need 1/4 of the elements, and only values with $|m′| ≤ m′ₘₐₓ$ will be computed.  This is particularly useful for computing spin-weighted spherical harmonics.

Note that the recursion coefficients `H_rec_coeffs` should be the quantity returned by [`H_recursion_coefficients`](@ref).
