```
smoothing(;
    npd :: Union{IMERGHalfHourly},
    geo :: GeoRegion = GeoRegion("GLB");
    spatial  :: Bool = false,
    temporal :: Bool = false,
    hours     :: Real = 0,
    smoothlon :: Real = 0,
    smoothlat :: Real = 0,
    verbose :: Bool = false
)
```

Perform spatialtemporal smoothing of the NASAPrecipitation dataset over the dates specified in the `npd` NASAPrecipitationDataset and `geo` GeoRegion.

# Keyword arguments

  * `spatial` : If `true`, perform spatial smoothing
  * `temporal` : If `true`, perform temporal smoothing
  * `hours` : The number of hours that temporal smoothing is performed over. Must be an integer multiple of the timestep.
  * `smoothlon` : The number of longitude degrees to smooth over. Must be an integer multiple of the `npd` dataset resolution.
  * `smoothlat` : The number of latitude degrees to smooth over. Must be an integer multiple of the `npd` dataset resolution.
  * `verbose` : If `true`, then do extra logging
