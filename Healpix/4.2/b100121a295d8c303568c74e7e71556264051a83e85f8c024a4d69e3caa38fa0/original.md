```
map2alm(map::HealpixMap{Float64, RingOrder, AA};
    lmax=nothing, mmax=nothing, niter::Integer=3)
map2alm(m::HealpixMap{T, RingOrder, AA}; lmax=nothing, mmax=nothing,
    niter::Integer=3) where {T <: Real, AA <: AbstractArray{T, 1} }
```

Compute the spherical harmonic coefficients of a map. To enhance precision, more iterations of the transforms can be performed by passing a nonzero `niter`. The underlying SHT library libsharp performs all calculations using `Cdouble` types, so all inputs are converted to types based on Float64.

# Arguments

  * `map`: the map to decompose in spherical harmonics. It can either be a `HealpixMap{T, RingOrder, AA}` type (scalar map) or a `PolarizedHealpixMap{T, RingOrder, AA}` type (polarized map).

# Keywords

  * `lmax::Integer`: the maximum ℓ coefficient, will default to 3*nside-1 if not specified.
  * `mmax::Integer`: the maximum m coefficient
  * `niter::Integer`: number of SHT iterations, to enhance precision. Defaults to 3

# Returns

  * `Alm{ComplexF64, Array{ComplexF64, 1}}`: the spherical harmonic coefficients corresponding to the map
