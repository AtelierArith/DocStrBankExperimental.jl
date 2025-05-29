```
RegionGrid(
    e5geo :: ERA5Region{ST,FT},
    lon   :: Vector{<:Real},
    lat   :: Vector{<:Real}
) -> GeoRegion.RegionGrid
```

Creates a RegionGrid containing information and mask information required to extract regional data for the ERA5Region from the raw data.

# Arguments

  * `e5geo` : A ERA5Region struct type
  * `lon`   : A vector containing the longitude points
  * `lat`   : A vector containing the latitude points
