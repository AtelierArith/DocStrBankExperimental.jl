```
mask!(m::HealpixMap, mask)
mask!(m::PolarizedHealpixMap, maskT, maskP)
```

Mask a map or polarized map in place.

# Arguments:

  * `m::Union{HealpixMap,PolarizedHealpixMap}`: map or polarized map to mask
  * `maskT::HealpixMap`: mask for first map's intensity
  * `maskP::HealpixMap`: mask for first map's polarization
