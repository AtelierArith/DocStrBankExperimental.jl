```Julia
impedance(U::UnitSystem,S::UnitSystem) = specificimpedance(U,S)/area(U,S)
impedance(v::Real,U::UnitSystem,S::UnitSystem) = v/impedance(U,S)
```

音響の `impedance` (Rayl⋅m⁻², Pa⋅s⋅m⁻³, kg⋅s⁻¹⋅m⁻⁴)、単位変換係数。

```Julia
julia> impedance(CGS,Metric) # Pa⋅cm³⋅m⁻³⋅Ba⁻¹
99999.99999999991

julia> impedance(English,Metric) # Pa⋅ft⁵⋅m⁻³⋅lb⁻¹
1690.8753884291211
```
