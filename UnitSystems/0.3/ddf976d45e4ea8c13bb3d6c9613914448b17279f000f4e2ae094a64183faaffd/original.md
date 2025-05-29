```Julia
admittance(U::UnitSystem,S::UnitSystem) = area(U,S)/specificimpedance(U,S)
admittance(v::Real,U::UnitSystem,S::UnitSystem) = v/admittance(U,S)
```

Acoustic `admittance` (m²⋅Rayl⁻¹, m³⋅s⁻¹⋅Pa⁻¹, m⁴⋅s⋅kg⁻¹), unit conversion factor.

```Julia
julia> admittance(CGS,Metric) # Ba⋅m³⋅cm⁻³⋅Pa⁻¹
1.0000000000000008e-5

julia> admittance(English,Metric) # lb⋅m³⋅ft⁻⁵⋅Pa⁻¹
0.0005914096371874174
```
