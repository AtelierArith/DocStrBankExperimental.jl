```Julia
inertance : [ML⁻⁴], [FL⁻⁵T²], [ML⁻⁴], [ML⁻⁴], [ML⁻⁴]
inertance(U::UnitSystem,S::UnitSystem) = mass(U,S)/length(U,S)^4
inertance(v::Real,U::UnitSystem,S::UnitSystem) = v/inertance(U,S)
ML⁻⁴ [ħ⁻⁴𝘤⁴mₑ⁵ϕ⁻⁴g₀⁻⁴] 統一

音響質量または `inertance` (kg⋅m⁴, Pa⋅s²⋅m⁻³)、単位換算係数。

```

Julia julia> inertance(CGS,Metric) # kg⋅cm⁴⋅g⁻¹⋅m⁻⁴ 2⁵5⁵ = 100000.0 [kg⋅m⁻⁴]/[g⋅cm⁻⁴] ガウス -> メトリック

julia> inertance(CGS,English) # slug⋅cm⁴⋅g⁻¹⋅ft⁻⁴ ft⁴lb⁻¹2⁵5⁵ = 1902.804238360888 [lbm⋅ft⁻⁴]/[g⋅cm⁻⁴] ガウス -> 英語

julia> inertance(English,Metric) # kg⋅ft⁴⋅lb⁻¹⋅m⁻⁴ ft⁻⁴lb = 52.55401369409494 [kg⋅m⁻⁴]/[lbm⋅ft⁻⁴] 英語 -> メトリック ```
