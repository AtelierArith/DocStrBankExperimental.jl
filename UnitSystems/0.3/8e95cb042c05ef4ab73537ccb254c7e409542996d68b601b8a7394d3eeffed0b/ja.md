```Julia
density(U::UnitSystem,S::UnitSystem) = mass(U,S)/volume(U,S)
density(v::Real,U::UnitSystem,S::UnitSystem) = v/density(U,S)
```

特定の質量または `mass` あたりの `volume` または `density` (kg⋅m⁻³)、単位変換係数。

```Julia
julia> density(CGS,Metric) # kg⋅cm³⋅g⁻¹⋅m⁻³
999.9999999999994

julia> density(CGS,Brtish) # slug⋅cm³⋅g⁻¹⋅ft⁻³
1.940320331979716

julia> density(English,Metric) # kg⋅ft³⋅lb⁻¹⋅m⁻³
16.018463373960138
```
