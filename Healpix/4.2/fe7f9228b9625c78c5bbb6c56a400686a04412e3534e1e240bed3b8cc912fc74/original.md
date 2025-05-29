```
applyFullWeights!(m::HealpixMap{T, RingOrder}, [wgt::Vector{T}]) where T
```

Apply a pixel weighting to a map for more accurate SHTs. Note that  this only helps for `lmax<=1.5*Nside`. If this is not the case, the  pixel weights may do more harm than good.

Pixel weights are automatically downloaded if not specified. 

# Arguments:

  * `m::HealpixMap{T, RingOrder}`: map to modify
  * `wgt::Vector{T}` (optional): compressed pixel weights. If not specified, this routine will   look for weights in artifacts.
