```
applyFullWeights!(m::PolarizedHealpixMap{T, RingOrder}, [wgt::Vector{T}]) where T
```

Apply a pixel weighting to a polarized map for more accurate SHTs.

# Arguments:

  * `m::PolarizedHealpixMap{T, RingOrder}`: map to modify
  * `wgt::Vector{T}` (optional): compressed pixel weights. If not specified, an artifact        will be sought.
