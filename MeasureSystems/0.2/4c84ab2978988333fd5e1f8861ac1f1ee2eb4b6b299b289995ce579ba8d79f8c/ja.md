```Julia
インピーダンス : [FL⁻⁵T], [FL⁻⁵T], [ML⁻⁴T⁻¹], [ML⁻⁴T⁻¹], [ML⁻⁴T⁻¹]
インピーダンス(U::UnitSystem,S::UnitSystem) = specificimpedance(U,S)/area(U,S)
インピーダンス(v::Real,U::UnitSystem,S::UnitSystem) = v/impedance(U,S)
FL⁻⁵T [ħ⁻⁵𝘤⁶mₑ⁶ϕ⁻⁵g₀⁻⁶] 統一

音響 `インピーダンス` (Rayl⋅m⁻², Pa⋅s⋅m⁻³, kg⋅s⁻¹⋅m⁻⁴)、単位換算係数。

```

Julia julia> インピーダンス(CGS,Metric) # Pa⋅cm³⋅m⁻³⋅Ba⁻¹ 2⁵5⁵ = 100000.0 [kg⋅m⁻⁴s⁻²]/[g⋅cm⁻⁴s⁻²] Gauss -> Metric

julia> インピーダンス(English,Metric) # Pa⋅ft⁵⋅m⁻³⋅lb⁻¹ g₀⋅ft⁻⁵lb = 1690.875388429121 [kg⋅m⁻⁴s⁻²]/[lbf⋅ft⁻⁵] English -> Metric ```
