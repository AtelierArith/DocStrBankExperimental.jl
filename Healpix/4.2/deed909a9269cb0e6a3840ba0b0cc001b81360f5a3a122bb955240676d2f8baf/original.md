```
synalm(cl::Vector{T}, lmax::Integer, mmax::Integer, rng::AbstractRNG) where {T <: Real}
synalm(cl::Vector{T}, lmax::Integer, mmax::Integer) where {T <: Real}
synalm(cl::Vector{T}, lmax::Integer, rng::AbstractRNG) where {T <: Real}
synalm(cl::Vector{T}, lmax::Integer) where {T <: Real}
synalm(cl::Vector{T}, rng::AbstractRNG) where {T <: Real}
synalm(cl::Vector{T}) where {T <: Real}
```

Generate a set of $a_{\ell m}$ from a given power spectra $C_{\ell}$. The output is written into a new `Alm` object of given lmax.

# Arguments:

  * `cl::AbstractVector{T}`: The array representing the power spectrum components $C_{\ell}$,

starting from $\ell = 0$.

  * `lmax::Integer`: the maximum $ℓ$ coefficient, will default to `length(cl)-1` if not specified.
  * `mmax::Integer`: the maximum $m$ coefficient, will default to `lmax` if not specified.
  * `rng::AbstractRNG` : (optional) the RNG to be used for generating the $a_{\ell m}$. It allows

to set the seed beforehand guaranteeing the reproducibility of the process.
