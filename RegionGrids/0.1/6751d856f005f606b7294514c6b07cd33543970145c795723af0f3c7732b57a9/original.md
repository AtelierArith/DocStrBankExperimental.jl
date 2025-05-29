```
RegionGrid(
    geo :: GeoRegion,
    lon :: Union{Vector{<:Real},AbstractRange{<:Real},
    lat :: Union{Vector{<:Real},AbstractRange{<:Real};
    rotation  :: Real = 0,
    sigdigits :: Int = 10
) -> ggrd :: RectilinearGrid
```

Creates a `RectilinearGrid` type based on the following arguments. This method is suitable for rectilinear grids of longitude/latitude output such as from Isca, or from satellite and reanalysis gridded datasets.

# Arguments

  * `geo` : A GeoRegion of interest.
  * `lon` : A vector or `AbstractRange` containing the longitude points.
  * `lat` : A vector or `AbstractRange` containing the latitude points.

# Keyword Arguments

  * `rotation` : Angle (in degrees) of rotation for the final "derotated" data about the GeoRegion centroid and projected into the X-Y cartesian coordinate system (in meters). A positive value relative to `geo.θ` will turn the final values about the centroid in the anti-clockwise direction. Default is 0.

# Returns

  * `ggrd` : A `RectilinearGrid`.
