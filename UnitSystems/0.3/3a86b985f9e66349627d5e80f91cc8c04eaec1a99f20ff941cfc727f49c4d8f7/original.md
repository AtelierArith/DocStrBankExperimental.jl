```Julia
inertance(U::UnitSystem,S::UnitSystem) = mass(U,S)/length(U,S)^4
inertance(v::Real,U::UnitSystem,S::UnitSystem) = v/inertance(U,S)
```

Acoustic mass or `inertance` (kg⋅m⁴, Pa⋅s²⋅m⁻³), unit conversion factor.

```Julia
julia> inertance(CGS,Metric) # kg⋅cm⁴⋅g⁻¹⋅m⁻⁴
99999.99999999991

julia> inertance(CGS,English) # slug⋅cm⁴⋅g⁻¹⋅ft⁻⁴
1902.8042383608874

julia> inertance(English,Metric) # kg⋅ft⁴⋅lb⁻¹⋅m⁻⁴
52.554013694094934
```
