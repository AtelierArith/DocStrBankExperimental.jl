```Julia
torr(U::UnitSystem) = pressure(atm/𝟐^3/𝟓/𝟏𝟗,U,Metric)
```

Unit of `pressure` exerted by 1 mm of mercury at standard atmospheric conditions.

```Julia
juila> torr(Metric) # Pa
133.32236842105263

julia> torr(English) # lb⋅ft⁻²
2.784495557465706

julia> torr(IPS) # lb⋅in⁻²
0.019336774704622972
```
