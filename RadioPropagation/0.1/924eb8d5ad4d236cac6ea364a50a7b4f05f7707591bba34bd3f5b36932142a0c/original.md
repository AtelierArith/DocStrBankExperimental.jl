```
fog_attenuation_db_per_km( frequency_ghz::Real, M, T_deg::Real )::Real
```

Empirical model for rain attenuation for frequencies above 5 GHz. One-way attenuation in dB/km.

# Arguments

  * `frequency_ghz`	The frequency of the propagating waves.
  * `M`				The watewater concentration in g/m³.
  * `T_deg`			The air temperature in degree Celsius.

## Examples

```jldoctest
julia> res = fog_attenuation_db_per_km( 10, 0.8, 23 );

julia> round(res, digits=6)
4.68976
```

## References

  * M. A. Richards and J. A. Scheer and W. A. Holm, Principles of Modern Radar, SciTech Publishing, 2010.
