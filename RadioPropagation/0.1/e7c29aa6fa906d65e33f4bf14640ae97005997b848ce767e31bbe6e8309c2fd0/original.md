```
atmospheric_attenuation_db_per_km( frequency_ghz::Real, T_kelvin::Real=288.15, water_vapour_density_g_m³::Real=7.5, dry_air_pressure_h_pa::Real=1013.25 )::Real
```

Empirical model for amospheric gaseous attenuation for frequencies in the range 1 - 1000 GHz. One-way attenuation in dB/km.

# Arguments

  * `frequency_ghz`				The frequency of the propagating waves.
  * `T_kelvin`					The absolute temperature in kelvin.
  * `water_vapour_density_g_m³` 	The water vapur density in g/m³.
  * `dry_air_pressure_h_pa`		The dry air pressure in hpa.

## Examples

```jldoctest
julia> res = atmospheric_attenuation_db_per_km( 22 );

julia> round(res, digits=6)
0.187337
```

## References

  * Rec. ITU-R P.676-12, Attenuation by atmospheric gases and related effects, ITU-R 2020.
