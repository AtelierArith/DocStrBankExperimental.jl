```
RegionGrid(
    geo :: Union{RectRegion,PolyRegion},
    lon :: Union{Vector{<:Real},AbstractRange{<:Real},
    lat :: Union{Vector{<:Real},AbstractRange{<:Real}
) -> ggrd :: RLinearMask
```

Creates a `RectGrid` or `PolyGrid` type based on the following arguments. This method is suitable for rectilinear grids of longitude/latitude output such as from Isca, or from satellite and reanalysis gridded datasets.

# Arguments

  * `geo` : A GeoRegion of interest
  * `lon` : A vector or `AbstractRange` containing the longitude points
  * `lat` : A vector or `AbstractRange` containing the latitude points

# Returns

  * `ggrd` : A `RectilinearGrid`
