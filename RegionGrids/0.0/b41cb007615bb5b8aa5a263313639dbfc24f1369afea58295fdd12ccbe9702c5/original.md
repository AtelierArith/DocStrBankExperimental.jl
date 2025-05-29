```
RegionGrid(
    geo  :: TiltRegion,
    pnts :: Array{Point2{FT}}
) where FT <: Real -> ggrd :: GeneralTilt
```

Creates a `GeneralTilt` type based on the following arguments. This method is more suitable for structured non-rectilinear (e.g., curvilinear) grids of longitude and latitude points, such as in the output of WRF.

# Arguments

  * `geo` : A GeoRegion of interest
  * `pnts` : An array of `Point2` types containing the longitude/latitude points

# Returns

  * `ggrd` : A `GeneralTilt`
