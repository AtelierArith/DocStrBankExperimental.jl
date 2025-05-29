```
extract(
    npd  :: NASAPrecipitationDataset,
    sgeo :: GeoRegion,
    pgeo :: GeoRegion,
) -> nothing
```

Extracts NASAPrecipitation data for a GeoRegion `sgeo` from a bigger GeoRegion `pgeo`.

!!! note
    Data for the parent GeoRegion identified by `pgeo` must already exist, and `sgeo` must be fully within the bounds of `pgeo`.


# Arguments

  * `npd` : a `NASAPrecipitationDataset` specifying the dataset details and date download range
  * `sgeo` : a `GeoRegion` (see [GeoRegions.jl](https://github.com/GeoRegionsEcosystem/GeoRegions.jl)) that sets the geographic bounds of the data array in lon-lat
  * `pgeo` : a `GeoRegion` that is a "parent" of the `GeoRegion` of interest `sgeo`, in the sense that `sgeo` must be fully within `pgeo`.
