```
rain_attenuation_db_per_km_circular_pol( frequency_ghz::Real, fall_rate_mm_hour::Real )::Real
```

Empirical model for rain attenuation for frequencies between 1 and 400 GHz, circular polarization. Model uses closest frequency in the underlying data. One-way attenuation in dB/km.

# Arguments

  * `frequency_ghz`     	The frequency of the propagating waves.
  * `fall_rate_mm_hour`	The rain intensity [mm/h].

## Examples

```jldoctest
julia> res = rain_attenuation_db_per_km_circular_pol( 30, 20 );

julia> round(res, digits=6)
3.675503
```

## References

  * M. A. Richards and J. A. Scheer and W. A. Holm, Principles of Modern Radar, SciTech Publishing, 2010.
