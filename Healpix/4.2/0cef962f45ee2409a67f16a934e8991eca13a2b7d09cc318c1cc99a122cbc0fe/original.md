```
adjoint_map2alm!(alm::Alm{ComplexF64, Array{ComplexF64, 1}}, map::HealpixMap{Float64, RingOrder, Array{Float64, 1}})
adjoint_map2alm!(alm::Array{Alm{ComplexF64, Array{ComplexF64, 1}},1}, map::PolarizedHealpixMap{Float64, RingOrder, Array{Float64, 1}})
```

This function performs the spherical harmonic transform (Y^-1)^t = W^t Y = W Y on the map and places the results in the passed `alm` object. This function requires types derived from Float64, since it is done in-place.

# Arguments

  * `alm::Alm{ComplexF64, Array{ComplexF64, 1}}`: the spherical harmonic coefficients to perform the spherical harmonic transform on.
  * `map`: the map that will contain the result. It can either be a `HealpixMap{Float64, RingOrder, Array{Float64, 1}}` type (scalar map) or a `PolarizedHealpixMap{Float64, RingOrder, Array{Float64, 1}}` (polarized map).
