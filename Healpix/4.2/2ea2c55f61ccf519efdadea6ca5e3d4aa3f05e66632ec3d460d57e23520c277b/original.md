```
synalm!(cl::Vector{T}, alm::Alm{ComplexF64, Vector{ComplexF64}}, rng::AbstractRNG) where {T <: Real}
synalm!(cl::Vector{T}, alm::Alm{ComplexF64, Vector{ComplexF64}}) where {T <: Real}
```

Generate a set of $a_{\ell m}$ from a given power spectra $C_{\ell}$. The output is written into the `Alm` object passed in input.

# Arguments:

  * `cl::AbstractVector{T}`: The array representing the power spectrum components $C_{\ell}$,

starting from $\ell = 0$.

  * `alm::Alm{Complex{T}}`: The array representing the spherical harmonics coefficients $a_{\ell m}$

we want to write the result into.

  * `rng::AbstractRNG` : (optional) the RNG to be used for generating the $a_{\ell m}$. It allows

to set the seed beforehand guaranteeing the reproducibility of the process.
