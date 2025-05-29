```Julia
specificimpedance : [FL⁻³T], [FL⁻³T], [ML⁻²T⁻¹], [ML⁻²T⁻¹], [ML⁻²T⁻¹]
specificimpedance(U::UnitSystem,S::UnitSystem) = pressure(U,S)/speed(U,S)
specificimpedance(v::Real,U::UnitSystem,S::UnitSystem) = v/specificimpedance(U,S)
FL⁻³T [ħ⁻³𝘤⁴mₑ⁴ϕ⁻³g₀⁻⁴] 統一

```

特性特定音響インピーダンス (Rayl, Pa⋅s⋅m⁻¹)、単位換算係数。

```Julia
julia> specificimpedance(CGS,Metric) # Pa⋅cm⋅m⁻¹⋅Ba⁻¹
2⋅5 = 10.0 [kg⋅m⁻²s⁻²]/[g⋅cm⁻²s⁻²] ガウス -> メトリック

julia> specificimpedance(English,Metric) # Pa⋅ft³⋅m⁻¹⋅lb⁻¹
g₀⋅ft⁻³lb = 157.08746384624618 [kg⋅m⁻²s⁻²]/[lbf⋅ft⁻³] 英語 -> メトリック
```
