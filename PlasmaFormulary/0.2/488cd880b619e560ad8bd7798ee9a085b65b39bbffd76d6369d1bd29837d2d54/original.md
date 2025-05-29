```
plasma_frequency(n::NumberDensity, [q::Charge, mass::Mass])
plasma_frequency(n::NumberDensity, p::ParticleLike; kw...)
```

Calculate the plasma frequency of a species.

The plasma frequency is a characteristic frequency of the plasma.  More often, it refers to the frequency at which electrons oscillate in the plasma.

# Examples

```jldoctest; filter = r"(\^-1|⁻¹)"
julia> plasma_frequency(1e19u"m^-3")  # plasma frequency
1.7839863654934653e11 rad s⁻¹

julia> plasma_frequency(1e19u"m^-3", :p)  # proton plasma frequency
4.1632945624883513e9 rad s⁻¹
```

# References

  * [Wikipedia](https://en.wikipedia.org/wiki/Plasma_oscillation)
  * [PlasmaPy Documentation](https://docs.plasmapy.org/en/latest/api/plasmapy.formulary.frequencies.plasma_frequency.html)
