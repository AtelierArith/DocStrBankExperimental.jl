```
synfast!(cl::Vector{T}, map::HealpixMap{T, RingOrder}, lmax::Integer, rng::AbstractRNG) where {T <: Real}
synfast!(cl::Vector{T}, map::HealpixMap{T, RingOrder}, lmax::Integer) where {T <: Real}
synfast!(cl::Vector{T}, map::HealpixMap{T, RingOrder}, rng::AbstractRNG) where {T <: Real}
synfast!(cl::Vector{T}, map::HealpixMap{T, RingOrder}) where {T <: Real}
```

Generate a map from a given power spectra $C_{\ell}$. The result is saved into the `HealpixMap` passed in input.

# Arguments:

  * `cl::AbstractVector{T}`: The array representing the power spectrum components $C_{\ell}$.
  * `map::HealpixMap{T, RingOrder}`: the map that will contain the result.
  * `lmax::Integer`: the maximum $ℓ$ coefficient, will default to `length(cl)-1` if not specified.
  * `rng::AbstractRNG` : (optional) the RNG to be used for generating the $a_{\ell m}$. It allows

to set the seed beforehand guaranteeing the reproducibility of the process.
