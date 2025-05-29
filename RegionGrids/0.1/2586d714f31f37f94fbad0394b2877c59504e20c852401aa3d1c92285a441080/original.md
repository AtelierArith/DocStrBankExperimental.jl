```
RegionGrid(
    geo  :: GeoRegion,
    pnts :: Array{Point2{FT}};
    rotation  :: Real = 0,
    sigdigits :: Int = 10
) where FT <: Real -> ggrd :: GeneralizedGrid
```

Creates a `GeneralizedGrid` type based on the following arguments. This method is more suitable for structured non-rectilinear (e.g., curvilinear) grids of longitude and latitude points, such as in the output of WRF.

# Arguments

  * `geo` : A GeoRegion of interest.
  * `pnts` : An array of `Point2(lon,lat)` types.

# Keyword Arguments

  * `rotation` : Angle (in degrees) of rotation for the final "derotated" data about the GeoRegion centroid and projected into the X-Y cartesian coordinate system (in meters). A positive value relative to `geo.θ` will turn the final values about the centroid in the anti-clockwise direction. Default is 0.

# Returns

  * `ggrd` : A `GeneralizedGrid`.
