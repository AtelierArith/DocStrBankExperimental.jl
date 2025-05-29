```
RegionGrid(
    geo  :: GeoRegion,
    pnts :: Vector{Point2{FT}};
    rotation  :: Real = 0,
    sigdigits :: Int = 10
) where FT <: Real -> ggrd :: UnstructuredGrid
```

Creates a `UnstructuredGrid` type. This method is more suitable for unstructured grids and mesh grid of longitude and latitude points, such as in the output of CESM2 when it is run in the cubed-sphere configuration.

# Arguments

  * `geo` : A GeoRegion of interest.
  * `pnts` : A `Vector` of `Point2(lon,lat)` types.

# Keyword Arguments

  * `rotation` : Angle (in degrees) of rotation for the final "derotated" data about the GeoRegion centroid and projected into the X-Y cartesian coordinate system (in meters). A positive value relative to `geo.θ` will turn the final values about the centroid in the anti-clockwise direction. Default is 0.

# Returns

  * `ggrd` : A `UnstructuredGrid`.
