```
RegionGrid(
    geo  :: TiltRegion,
    pnts :: Vector{Point2{FT}}
) where FT <: Real -> ggrd :: VectorTilt
```

Creates a `VectorTilt` type based on a vector of 

# Arguments

  * `geo` : A GeoRegion of interest
  * `pnts` : A `Vector` of `Float` Types, containing the longitude points

# Returns

  * `ggrd` : A `VectorTilt`
