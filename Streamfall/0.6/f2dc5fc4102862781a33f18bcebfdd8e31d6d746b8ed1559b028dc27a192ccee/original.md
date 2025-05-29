```
calc_ET_from_T(e::F, T::F, Mf::F, f::F, d::F)::F where {F<:Float64}
```

Calculate evapotranspiration based on temperature data.

Parameters `f` and `d` are used to calculate `g`, the value of the CMD which the ET rate will begin to decline due to insufficient water availability for plant transpiration.

# Arguments

  * `e`: temperature to PET conversion factor (a stress threshold)
  * `T`: temperature in degrees C
  * `Mf`: Catchment Moisture Deficit prior to accounting for ET losses (`Mf`)
  * `f`: multiplication factor on `d`
  * `d`: flow threshold factor

# Returns

Estimate of ET from temperature (for catchment area)
