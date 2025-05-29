```Julia
action : [FLT], [FLT], [ML²T⁻¹], [ML²T⁻¹], [ML²T⁻¹]
action(U::UnitSystem,S::UnitSystem) = energy(U,S)*time(U,S)
action(v::Real,U::UnitSystem,S::UnitSystem) = v/action(U,S)
FLT [ħ⋅ϕ] 統一

長さに対する`運動量`または`作用` (J⋅s, N⋅m⋅s)、単位換算係数。

```

Julia julia> action(CGS,Metric) # J⋅erg⁻¹ 2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] ガウス -> メトリック

julia> action(CGS,English) # ft⋅lb⋅erg⁻¹ g₀⁻¹ft⁻¹lb⁻¹2⁻⁷5⁻⁷ = 7.375621492772652×10⁻⁸ [lbf⋅ft]/[erg] ガウス -> 英語

julia> action(English,Metric) # J⋅ft⁻¹⋅lb⁻¹ g₀⋅ft⋅lb = 1.3558179483314003 [J]/[lbf⋅ft] 英語 -> メトリック ```
