```Julia
flick(U::UnitSystem) = radiance(𝟏𝟎^10,U,Metric)/length(𝟏,U,Metric)
```

ロッキード・マーチンの `radiance` の単位は `length` あたり (W⋅m⁻³⋅rad⁻²) です。

```Julia
julia> flick(Metric) # W⋅m⁻³
1.0e10

julia> flick(CGS) # erg⋅s⁻¹⋅mL⁻¹
1.0000000000000006e11

julia> flick(MetricSpatian) # W⋅m⁻³⋅ς⁻²
1.2566370614359174e11
```
