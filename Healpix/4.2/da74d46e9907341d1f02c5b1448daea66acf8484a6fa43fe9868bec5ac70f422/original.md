```
gaussbeam(fwhm::T, lmax::Int; pol=false) where T
```

Compute the Gaussian beam window function $B_{\ell}$ given the FWHM of the beam in radians, where $C_{\ell, \mathrm{measured}} = B_{\ell}^2 C_{\ell}$. This beam is valid in the limit of $\sigma^2 \ll 0$, which is the case for all high-resolution CMB experiments.

# Arguments

  * `fwhm::T`: FWHM of the Gaussian beam in radians
  * `lmax::Int`: maximum multipole ℓ
  * `pol=false`: if false, returns the spin-0 beam for i.e. intensity. if true, returns the spin-2 beam

# Returns

  * `Array{T,1}` containing $B_{\ell}$, with the first element referring to ℓ=0.
