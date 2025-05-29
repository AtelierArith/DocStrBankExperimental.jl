```Julia
area : [L²], [L²], [L²], [L²], [L²]
area(U::UnitSystem,S::UnitSystem) = length(U,S)^2
area(v::Real,U::UnitSystem,S::UnitSystem) = v/area(U,S)
L² [ħ²𝘤⁻²mₑ⁻²ϕ²g₀²] 統一

二次元形状の範囲または `area` (m²)、単位換算係数。

```

Julia julia> area(CGS,Metric) # m²⋅cm⁻² 2⁻⁴5⁻⁴ = 0.0001 [m²]/[cm²] ガウス -> メトリック

julia> area(English,Metric) # m²⋅ft⁻² ft² = 0.09290304 [m²]/[ft²] 英語 -> メトリック

julia> area(Survey,English) # ft²⋅ftUS⁻² ft⁻²ftUS² = 1.0000040000119996 [ft²]/[ft²] サーベイ -> 英語 ```
