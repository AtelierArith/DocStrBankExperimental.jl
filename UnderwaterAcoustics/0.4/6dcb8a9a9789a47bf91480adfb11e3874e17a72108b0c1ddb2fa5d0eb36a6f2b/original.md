```
UnderwaterEnvironment(; kwargs...)
```

Create a generic underwater environment with the given parameters. The following parameters are supported:

  * `bathymetry` = bathymetry model
  * `altimetry` = altimetry model
  * `temperature` = temperature model
  * `salinity` = salinity model
  * `soundspeed` = sound speed profile model
  * `density` = density model
  * `seabed` = seabed sediment model
  * `surface` = surface model

All parameters are optional and have default values. Parameters may be modified after construction by setting the corresponding property in the environment.
