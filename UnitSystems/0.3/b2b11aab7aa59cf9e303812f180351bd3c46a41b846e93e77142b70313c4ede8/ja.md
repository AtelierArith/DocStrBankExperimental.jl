```Julia
areadensity(U::UnitSystem,S::UnitSystem) = mass(U,S)/area(U,S)
areadensity(v::Real,U::UnitSystem,S::UnitSystem) = v/areadensity(U,S)
```

表面または `areadensity` または `mass` あたり `area` (kg⋅m⁻²)、単位変換係数。

```Julia
julia> areadensity(CGS,Metric) # kg⋅cm²⋅g⁻¹⋅m⁻²
9.999999999999996

julia> areadensity(CGS,English) # lb⋅cm²⋅g⁻¹⋅ft⁻²
2.0481614362252167

julia> areadensity(English,Metric) # kg⋅ft²⋅lb⁻¹⋅m⁻²
4.88242763638305

julia> areadensity(British,Metric) # kg⋅ft²⋅slug⁻¹⋅m⁻²
157.08746384624612
```
