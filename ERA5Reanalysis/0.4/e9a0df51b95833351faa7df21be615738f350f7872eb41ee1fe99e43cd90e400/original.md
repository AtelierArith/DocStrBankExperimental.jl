```
RegionGrid(
    e5geo :: ERA5Region{ST,FT},
    lon   :: Array{<:Real},
    lat   :: Array{<:Real}
) -> GeoRegion.RegionGrid
```

Creates a RegionGrid containing information and mask information required to extract regional data for the ERA5Region from the raw data.

# Arguments

  * `e5geo` : A ERA5Region struct type
  * `lon`   : An array containing the longitude points
  * `lat`   : An array containing the latitude points
