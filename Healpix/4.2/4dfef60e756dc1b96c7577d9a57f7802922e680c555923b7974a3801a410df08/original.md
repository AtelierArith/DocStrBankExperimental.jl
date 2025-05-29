```
synfast(cl::Vector{T}, nside::Integer, lmax::Integer, rng::AbstractRNG) where {T <: Real}
synfast(cl::Vector{T}, nside::Integer, lmax::Integer) where {T <: Real}
synfast(cl::Vector{T}, nside::Integer, rng::AbstractRNG) where {T <: Real}
synfast(cl::Vector{T}, nside::Integer) where {T <: Real}
```

Generate a `HealpixMap` with given Nside, from a given power spectra $C_{\ell}$.

# Arguments:

  * `cl::AbstractVector{T}`: The array representing the power spectrum components $C_{\ell}$.
  * `nside::Integer`: nside of the map that will contain the result.
  * `lmax::Integer`: the maximum $ℓ$ coefficient, will default to `length(cl)`-1 if not specified.
  * `rng::AbstractRNG` : (optional) the RNG to be used for generating the $a_{\ell m}$. It allows

to set the seed beforehand guaranteeing the reproducibility of the process.
