```
mri_smap_fit(smaps, embed ; mask, kwargs...)
```

Fit MRI sensitivity maps `smaps` using `mri_smap_basis(mask ; kwargs...)`. Caller provides `ImageGeoms.embed` or equivalent.

Return named tuple `(B, ν, coefs, nrmse, smaps)`:

  * `(B, ν)` from `mri_smap_basis`
  * `coefs::Vector` : `[ncoil]` each of length `nk`
  * `nrmse::Real` : `smaps` vs `smaps_fit`
  * `smaps::Vector{Array{D}}` : `smaps_fit`
