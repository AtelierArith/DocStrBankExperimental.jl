```Julia
earthcalorie(U::UnitSystem) = calorie(U)*(sqrt(g₀/GME)/τ)^3*𝟐^27*𝟓^21
```

1 `earthgram` の水を `kelvin` で 1 度上昇させるのに必要な熱エネルギー（`Meridian` 単位）。

```Julia
julia> earthcalorie(Meridian) # J
4.174638363474497

julia> earthcalorie(Metric) # J
4.204951541946288

julia> earthcalorie(British) # ft⋅lb
3.101413096884655
```
