```
extract(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion
) -> nothing
```

Extracts NASAPrecipitation data for a GeoRegion `geo` from its parent GeoRegion `geo.pID`.

!!! note
    Data for the parent GeoRegion identified by `geo.pID` must already exist.


# Arguments

  * `npd` : a `NASAPrecipitationDataset` specifying the dataset details and date download range
  * `geo` : a `GeoRegion` (see [GeoRegions.jl](https://github.com/GeoRegionsEcosystem/GeoRegions.jl)) that sets the geographic bounds of the data array in lon-lat
