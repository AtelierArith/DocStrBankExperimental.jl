```
q_vap_from_RH_liquid(param_set, p, T, RH)
```

Computes the water vapor specific humidity from relative humidity with   regard to water (i.e. saturation vapor pressure over ice is not considered   even in cold temperatures).

Inputs:

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `p` pressure
  * `T` temperature
  * `RH` relative humidity
