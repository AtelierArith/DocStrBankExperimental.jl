```
PrescribedRadiativeFluxes{FT, SW, LW, DT, T, TP} <: AbstractRadiativeDrivers{FT}
```

Container for the prescribed radiation functions needed to drive land models in standalone mode.

Note that some models require the zenith angle AND diffuse fraction. The diffuse fraction may be provided directly (of type TimeVaryingInput), or it may be computed empirically. In the latter case, it requires the thermodynamic parameters as well to compute.

Therefore, the allowed combinations are:

1. Zenith angle and diffuse fraction not needed: zenith angle=nothing, thermo_params=nothing, diffuse fraction=nothing
2. Zenith angle provided and diffuse fraction computed empirically:  thermo params used, diffuse fraction=nothing
3. Zenith angle provided and diffuse fraction provided: thermo_params not used, diffuse fraction TimeVaryingInput

  * `SW_d`: Downward shortwave radiation function of time (W/m^2): positive indicates towards surface
  * `frac_diff`: Diffuse Fraction of shortwave radiation (unitless, [0,1])
  * `LW_d`: Downward longwave radiation function of time (W/m^2): positive indicates towards surface
  * `start_date`: Start date - the datetime corresponding to t=0 for the simulation
  * `θs`: Sun zenith angle, in radians
  * `thermo_params`: Thermodynamic parameters
