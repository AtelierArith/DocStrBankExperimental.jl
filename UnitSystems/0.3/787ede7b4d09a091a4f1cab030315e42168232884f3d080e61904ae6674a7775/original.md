```Julia
earthcalorie(U::UnitSystem) = calorie(U)*(sqrt(g₀/GME)/τ)^3*𝟐^27*𝟓^21
```

Heat energy required to raise 1 `earthgram` of water by 1 `kelvin` in `Meridian` units.

```Julia
julia> earthcalorie(Meridian) # J
4.174638363474497

julia> earthcalorie(Metric) # J
4.204951541946288

julia> earthcalorie(British) # ft⋅lb
3.101413096884655
```
