```Julia
barn(U::UnitSystem) = area((𝟐*𝟓)^-28,U,Metric)
```

面積の単位は `100` 平方フェムトメートル (m² または ft²) で定義されています。

```Julia
julia> barn(Metric) # m²
1.0000000000000015e-28

julia> barn(CGS) # cm²
1.000000000000001e-24

julia> barn(English) # ft²
1.0763910416709738e-27
```
