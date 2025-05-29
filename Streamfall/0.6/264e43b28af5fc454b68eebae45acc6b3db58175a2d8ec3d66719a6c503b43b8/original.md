```
calc_ET_from_E(e::F, evap::F, Mf::F, f::F, d::F)::F where {F<:Float64}
```

Calculate evapotranspiration from evaporation.

# Arguments

  * `e`: temperature to PET conversion factor (a stress threshold)
  * `evap`: evaporation for given time step
  * `Mf`: Catchment Moisture Deficit prior to accounting for ET losses (`Mf`)
  * `f`: calibrated parameter that acts as a multiplication factor on `d`
  * `d`: flow threshold factor

# Returns

  * Estimate of ET
