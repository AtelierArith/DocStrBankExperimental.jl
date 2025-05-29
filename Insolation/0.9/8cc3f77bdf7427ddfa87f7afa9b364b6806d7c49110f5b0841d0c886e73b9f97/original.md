```
solar_flux_and_cos_sza(date::DateTime,
                  date0::DateTime,
                  od::OrbitalData,
                  longitude::FT,
                  latitude::FT,
                  param_set::IP.AIP) where {FT <: Real}
```

Returns the top-of-atmosphere (TOA) solar flux, i.e.  the total solar irradiance (TSI) weighted by the earth-sun distance and cos(solar zenith angle) for input to RRTMGP.jl param_set is an AbstractParameterSet from ClimaParams.jl.
