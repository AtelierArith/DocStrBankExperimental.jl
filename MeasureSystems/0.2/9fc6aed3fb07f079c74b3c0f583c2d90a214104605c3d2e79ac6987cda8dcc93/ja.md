```Julia
areadensity : [ML⁻²], [FL⁻³T²], [ML⁻²], [ML⁻²], [ML⁻²]
areadensity(U::UnitSystem,S::UnitSystem) = mass(U,S)/area(U,S)
areadensity(v::Real,U::UnitSystem,S::UnitSystem) = v/areadensity(U,S)
ML⁻² [ħ⁻²𝘤²mₑ³ϕ⁻²g₀⁻²] 統一

表面または `areadensity` または `mass` あたりの `area` (kg⋅m⁻²)、単位換算係数。

```

Julia julia> areadensity(CGS,Metric) # kg⋅cm²⋅g⁻¹⋅m⁻² 2⋅5 = 10.0 [kg⋅m⁻²]/[g⋅cm⁻²] ガウス -> メトリック

julia> areadensity(CGS,English) # lb⋅cm²⋅g⁻¹⋅ft⁻² ft²lb⁻¹2⋅5 = 2.048161436225217 [lbm⋅ft⁻²]/[g⋅cm⁻²] ガウス -> 英語

julia> areadensity(English,Metric) # kg⋅ft²⋅lb⁻¹⋅m⁻² ft⁻²lb = 4.88242763638305 [kg⋅m⁻²]/[lbm⋅ft⁻²] 英語 -> メトリック

julia> areadensity(British,Metric) # kg⋅ft²⋅slug⁻¹⋅m⁻² g₀⋅ft⁻³lb = 157.08746384624618 [kg⋅m⁻²]/[lb⋅ft⁻³s²] ブリティッシュ -> メトリック ```
