```Julia
diffusivity(U::UnitSystem,S::UnitSystem) = speed(U,S)*length(U,S)
diffusivity(v::Real,U::UnitSystem,S::UnitSystem) = v/diffusivity(U,S)
```

熱的 `diffusivity` または運動粘度 (m²⋅s⁻¹)、単位変換係数。

```Julia
julia> diffusivity(CGS,Metric) # m²⋅cm⁻²
0.00010000000000000002

julia> diffusivity(English,Metric) # m²⋅ft⁻²
0.09290304

julia> diffusivity(Survey,English) # ft²⋅ftUS⁻²
1.0000040000119998
```
