```
alm2map(alm::Alm{ComplexF64, Array{Float64, 1}}, nside::Integer)
alm2map(alm::Alm{T, Array{T, 1}}, nside::Integer) where T
alm2map(alm::Array{Alm{ComplexF64, Array{ComplexF64, 1}},1}, nside::Integer)
alm2map(alms::Array{Alm{T, Array{T, 1}},1}, nside::Integer) where T
```

Compute a map from spherical harmonic coefficients. The underlying SHT library libsharp performs all calculations in Cdouble, so all inputs are converted to types based on Float64.

# Arguments

  * `alm`: the spherical harmonic coefficients to transform. If of type `Alm{T, Array{T, 1}}`, we assume a spin-0 spherical harmonic transform. If an array of `Alm` is passed, we assume that the components correspond to T, E, and B coefficients.

# Keywords

  * `nside::Integer`: Healpix resolution parameter

# Returns

  * `HealpixMap{Float64, RingOrder, Array{Float64, 1}}` or `PolarizedHealpixMap{Float64, RingOrder, Array{Float64, 1}}` depending on if the input alm is of type `Alm{T, Array{T, 1}}` or `Array{Alm{T, Array{T, 1}}}` respectively.
