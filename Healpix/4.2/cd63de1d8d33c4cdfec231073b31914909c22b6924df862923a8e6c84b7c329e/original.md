```
map2alm!(map::HealpixMap{Float64, RingOrder, Array{Float64, 1}}, alm::Alm{ComplexF64, Array{ComplexF64, 1}}; niter::Integer=3)
map2alm!(map::PolarizedHealpixMap{Float64, RingOrder, Array{Float64, 1}}, alm::Array{Alm{ComplexF64, Array{ComplexF64, 1}},1};
    niter::Integer=3)
```

This function performs a spherical harmonic transform on the map and places the results in the passed `alm` object. This function requires types derived from Float64, since it is done in-place.

# Arguments

  * `map`: the map that must be decomposed in spherical harmonics. It can either be a `HealpixMap{Float64, RingOrder}` type (scalar map) or a `PolarizedHealpixMap{Float64, RingOrder}` type (polarized map).
  * `alm::Alm{ComplexF64, Array{ComplexF64, 1}}`: the spherical harmonic coefficients to be written to.

# Keywords

  * `niter::Integer`: number of iterations of SHTs to perform, to enhance accuracy
