```
rain_attenuation_db_per_km( polarization::Symbol, frequency_ghz::Real, fall_rate_mm_hour::Real )::Real
```

Empirical model for RF rain attenuation for frequencies between 1 and 400 GHz, linear polarization. Model uses the closest frequency in the underlying data.

# Arguments

  * `polarization`        The polarization, `:vertical`, `:horizontal`.
  * `frequency_ghz`     	The frequency of the propagating waves.
  * `fall_rate_mm_hour`	The rain intensity [mm/h].

## Examples

```jldoctest
julia> res = rain_attenuation_db_per_km( :vertical , 30, 20 );

julia> round(res, digits=6)
3.34
```

## References

  * M. A. Richards and J. A. Scheer and W. A. Holm, Principles of Modern Radar, SciTech Publishing, 2010.
