```
RegionGrid(
    geo  :: Union{RectRegion,PolyRegion},
    pnts :: Vector{Point2{FT}}
) where FT <: Real -> ggrd :: VectorMask
```

Creates a `VectorMask` type based on a vector of 

# Arguments

  * `geo` : A GeoRegion of interest
  * `pnts` : A `Vector` of `Float` Types, containing the longitude points

# Returns

  * `ggrd` : A `VectorMask`
