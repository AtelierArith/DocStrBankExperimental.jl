```Julia
admittance(U::UnitSystem,S::UnitSystem) = area(U,S)/specificimpedance(U,S)
admittance(v::Real,U::UnitSystem,S::UnitSystem) = v/admittance(U,S)
```

音響の `admittance` (m²⋅Rayl⁻¹, m³⋅s⁻¹⋅Pa⁻¹, m⁴⋅s⋅kg⁻¹)、単位変換係数。

```Julia
julia> admittance(CGS,Metric) # Ba⋅m³⋅cm⁻³⋅Pa⁻¹
1.0000000000000008e-5

julia> admittance(English,Metric) # lb⋅m³⋅ft⁻⁵⋅Pa⁻¹
0.0005914096371874174
```
