```
read(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion,
    dt  :: TimeType;
    smooth   :: Bool = false,
    smoothlon  :: Real = 0,
    smoothlat  :: Real = 0,
    smoothtime :: Real = 0,
    quiet  :: Bool = false
) -> NCDataset
```

Reads a NASA Precipitation dataset specified by `npd` for a GeoRegion specified by `geo` at a date specified by `dt`.

# Arguments

  * `npd` : a `NASAPrecipitationDataset` specifying the dataset details and date download range
  * `geo` : a `GeoRegion` (see [GeoRegions.jl](https://github.com/GeoRegionsEcosystem/GeoRegions.jl)) that sets the geographic bounds of the data array in lon-lat
  * `dt`  : A specified date. The NCDataset retrieved may will contain data for the date, although it may also contain data for other dates depending on the `NASAPrecipitationDataset` specified by `npd`

# Keyword Arguments

  * `smooth` :
  * `smoothlon` :
  * `smoothlat` :
  * `smoothtime` :
  * `quiet` :
