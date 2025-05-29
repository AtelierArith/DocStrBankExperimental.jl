```
smoothing(;
    npd :: Union{IMERGMonthly,TRMMMonthly},
    geo :: GeoRegion;
    smoothlon :: Real = 0,
    smoothlat :: Real = 0,
    verbose :: Bool = false
)
```

Perform spatial smoothing of the **Monthly* NASAPrecipitation dataset over the dates specified in the `npd` NASAPrecipitationDataset and `geo` GeoRegion.

!!! warning
    Temporal smoothing ***cannot*** be performed on IMERGMonthly and TRMMMonthly datasets. They can only be spatially smoothed.


# Keyword arguments

  * `smoothlon` : The number of longitude degrees to smooth over. Must be an integer multiple of the `npd` dataset resolution.
  * `smoothlat` : The number of latitude degrees to smooth over. Must be an integer multiple of the `npd` dataset resolution.
  * `verbose` : If `true`, then do extra logging
