```
mutable struct PolarizedHealpixMap{T, O <: Healpix.Order, AA <: AbstractArray{T, 1}}
```

A polarized I/Q/U map. It contains three Healpix maps with the same NSIDE:

  * `i`
  * `q`
  * `u`

You can create an instance of this type using the function [`PolarizedHealpixMap{T,O}`](@ref), which comes in three flavours:

  * `PolarizedHealpixMap(i::HealpixMap{T,O,AA}, q::HealpixMap{T,O,AA}, u::HealpixMap{T,O,AA})`
  * `PolarizedHealpixMap{T,O}(i::AbstractVector{T}, q::AbstractVector{T}, u::AbstractVector{T})`
  * `PolarizedHealpixMap{T,O}(nside::Number)`
