```Julia
torr(U::UnitSystem) = pressure(atm/𝟐^3/𝟓/𝟏𝟗,U,Metric)
```

標準大気条件下で1 mmの水銀によって加えられる`pressure`の単位。

```Julia
juila> torr(Metric) # Pa
133.32236842105263

julia> torr(English) # lb⋅ft⁻²
2.784495557465706

julia> torr(IPS) # lb⋅in⁻²
0.019336774704622972
```
