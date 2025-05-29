```
smoothing(;
    npd :: Union{IMERGDaily,TRMMDaily},
    geo :: GeoRegion;
    spatial  :: Bool = false,
    temporal :: Bool = false,
    days :: Int = 0,
    smoothlon :: Real = 0,
    smoothlat :: Real = 0,
    verbose :: Bool = false
)
```

Perform spatialtemporal smoothing of a daily NASAPrecipitation dataset over the dates specified in the `npd` NASAPrecipitationDataset and `geo` GeoRegion.

# Keyword arguments

  * `spatial` : If `true`, perform spatial smoothing
  * `temporal` : If `true`, perform temporal smoothing
  * `days` : The number of days that temporal smoothing is performed over. Must be an integer.
  * `smoothlon` : The number of longitude degrees to smooth over. Must be an integer multiple of the `npd` dataset resolution.
  * `smoothlat` : The number of latitude degrees to smooth over. Must be an integer multiple of the `npd` dataset resolution.
  * `verbose` : If `true`, then do extra logging
