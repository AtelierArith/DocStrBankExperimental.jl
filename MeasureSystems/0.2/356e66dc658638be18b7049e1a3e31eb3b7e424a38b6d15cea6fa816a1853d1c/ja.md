```Julia
回転慣性 : [ML²], [FLT²], [ML²], [ML²], [ML²]
回転慣性(U::UnitSystem,S::UnitSystem) = 質量(U,S)*面積(U,S)
回転慣性(v::Real,U::UnitSystem,S::UnitSystem) = v/回転慣性(U,S)
ML² [ħ²𝘤⁻²mₑ⁻¹ϕ²g₀²] 統一

```

慣性モーメントまたは `回転慣性` (kg⋅m²)、単位変換係数。

```Julia
julia> 回転慣性(CGS,Metric) # kg⋅m²⋅g⁻¹⋅cm⁻²
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [kg⋅m²]/[g⋅cm²] ガウス -> メトリック

julia> 回転慣性(CGS,British) # slug⋅ft²⋅g⁻¹⋅cm⁻²
g₀⁻¹ft⁻¹lb⁻¹2⁻⁷5⁻⁷ = 7.375621492772652×10⁻⁸ [lb⋅ft⋅s²]/[g⋅cm²] ガウス -> ブリティッシュ

julia> 回転慣性(English,Metric) # kg⋅m²⋅lb⁻¹⋅ft⁻²
ft²lb = 0.042140110093804806 [kg⋅m²]/[lbm⋅ft²] 英語 -> メトリック
```
