```Julia
compliance(U::UnitSystem,S::UnitSystem) = time(U,S)^2/mass(U,S)
compliance(v::Real,U::UnitSystem,S::UnitSystem) = v/compliance(U,S)
```

Acoustic `compliance` is reciprocal of `fluence` (m⋅N⁻¹, m³⋅Pa⁻¹), unit conversion factor.

```Julia
julia> compliance(CGS,Metric) # kg⋅g⁻¹
1000.0

julia> compliance(CGS,English) # slug⋅g⁻¹
453.5923700000001

julia> compliance(English,Metric) # kg⋅lb⁻¹
2.2046226218487757
```
