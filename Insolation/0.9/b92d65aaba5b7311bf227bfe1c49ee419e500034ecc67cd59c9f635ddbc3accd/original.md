```
daily_zenith_angle(date::DateTime,
                   data0::DateTime,
                   od::OrbitalData,
                   latitude::FT,
                   param_set::IP.AIP;
                   eot_correction::Bool=true,
                   milankovitch::Bool=true) where {FT <: Real}
```

Returns the effective zenith angle corresponding to the diurnally averaged insolation and earth-sun distance at a particular latitude given the date.

`param_set` is an AbstractParameterSet from ClimaParams.jl.

`eot_correction` is an optional Boolean keyword argument that defaults to true when set to true the equation of time correction is turned on. This switch functionality is implemented for easy comparisons with reanalyses.

`milankovitch` is an optional Boolean keyword argument that defaults to true when set to true the orbital parameters are calculated for the given DateTime, when set to false the orbital parameters at the J2000 epoch from ClimaParams are used.
