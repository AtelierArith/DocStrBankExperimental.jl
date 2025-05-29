```
make_weighted_healpix_geom_info(
    nside::Integer, stride::Integer, weight::AbstractArray{T}
    ) where T <: Real
```

Initialises a geometry structure corresponding to HEALPix.

# Arguments

  * `nside::Integer`: HEALPix resolution parameter
  * `stride::Integer`: the stride between consecutive pixels in the ring
  * `weight::AbstractArray{T}`: the weight that must be multiplied to every pixel    during a map analysis (typically the solid angle of a pixel in the ring)

# Returns

  * `GeomInfo` object
