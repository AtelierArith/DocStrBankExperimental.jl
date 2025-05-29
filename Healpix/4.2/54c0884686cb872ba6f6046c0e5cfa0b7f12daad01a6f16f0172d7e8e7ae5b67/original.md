```
adjoint_alm2map!(map::HealpixMap{Float64, RingOrder, Array{Float64, 1}}, alm::Alm{ComplexF64, Array{ComplexF64, 1}})
adjoint_alm2map!(map::PolarizedHealpixMap{Float64, RingOrder, Array{Float64, 1}}, alm::Array{Alm{ComplexF64, Array{ComplexF64, 1}},1})
```

This function performs a spherical harmonic transform Yᵀ on the map and places the results in the passed `alm` object. This function requires types derived from Float64, since it is done in-place.

# Arguments

  * `map`: the map that must be decomposed in spherical harmonics. It can either be a `HealpixMap{Float64, RingOrder}` type (scalar map) or a `PolarizedHealpixMap{Float64, RingOrder}` type (polarized map).
  * `alm::Alm{ComplexF64, Array{ComplexF64, 1}}`: the spherical harmonic coefficients to be written to.
