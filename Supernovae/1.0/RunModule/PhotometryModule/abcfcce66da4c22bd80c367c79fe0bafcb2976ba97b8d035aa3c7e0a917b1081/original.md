```
mutable struct Observation
```

A single observation of a supernova, including time, flux, magnitude and filter information.

# Fields

  * `name::String`: The name of the supernova
  * `time::typeof(1.0u"d")`: The time of the observation in MJD
  * `flux::typeof(1.0u"Jy")`: The flux of the observation in Jansky
  * `flux_err::typeof(1.0u"Jy")`: The flux error of the observation in Jansky
  * `mag::typeof(1.0u"AB_mag")`: The magnitude of the observations in AB Magnitude
  * `mag_err::typeof(1.0u"AB_mag")`: The magnitude error of the observations in AB Magnitude
  * `absmag::typeof(1.0u"AB_mag")`: The absolute magnitude of the observations in AB Magnitude
  * `absmag_err::typeof(1.0u"AB_mag")`: The absolute magnitude error of the observations in AB Magnitude
  * `filter::Filter`: The [`Filter`](@ref) used to observe the supernova
  * `is_upperlimit::Bool`: Whether the observation is an upperlimit
