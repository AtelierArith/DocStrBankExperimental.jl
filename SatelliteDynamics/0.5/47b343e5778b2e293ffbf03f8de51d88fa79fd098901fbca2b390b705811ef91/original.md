Module-wide global EarthOrientationData object. This data object is used as the default source of Earth Orientation Data by reference system transformations if no explicit EarthOrientationData file is provided to those transformations.

This value can be overridden in your own code as follows:

```julia
SatelliteDynamics.EOP = EarthOrientationData(:FINALS_2000)
```

This global variable defaults to use the module's internal version of `"FINALS_2000"`  if it is not otherwise set/provided.
