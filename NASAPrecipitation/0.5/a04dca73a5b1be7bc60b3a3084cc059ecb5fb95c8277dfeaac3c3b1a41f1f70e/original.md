```
download(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion = GeoRegion("GLB");
    overwrite :: Bool = false
) -> nothing
```

Downloads a NASA Precipitation dataset specified by `npd` for a GeoRegion specified by `geo`

# Arguments

  * `npd` : a `NASAPrecipitationDataset` specifying the dataset details and date download range
  * `geo` : a `GeoRegion` (see [GeoRegions.jl](https://github.com/GeoRegionsEcosystem/GeoRegions.jl)) that sets the geographic bounds of the data array in lon-lat

# Keyword Arguments

  * `overwrite` : If `true`, overwrite any existing files
