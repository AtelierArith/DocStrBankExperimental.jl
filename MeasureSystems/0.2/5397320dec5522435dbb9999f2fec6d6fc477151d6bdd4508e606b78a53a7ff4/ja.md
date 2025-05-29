```Julia
molarentropy : [FLΘ⁻¹N⁻¹], [FLΘ⁻¹N⁻¹], [ML²T⁻²Θ⁻¹N⁻¹], [ML²T⁻²Θ⁻¹N⁻¹], [ML²T⁻²Θ⁻¹N⁻¹]
molarentropy(U::UnitSystem,S::UnitSystem) = entropy(U,S)/molaramount(U,S)
molarentropy(v::Real,U::UnitSystem,S::UnitSystem) = v/molarentropy(U,S)
FLΘ⁻¹N⁻¹ [kB⋅mₑ⁻¹Mᵤ] 統一
```

モル熱容量または `molaramount` あたりの `entropy` (J⋅K⁻¹⋅mol⁻¹)、単位換算係数。

```Julia
julia> molarentropy(CGS,Metric) # J⋅erg⁻¹
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] ガウス -> メトリック

julia> molarentropy(English,SI2019) # J⋅°R⋅lb-mol⋅ft⁻¹⋅lb⁻¹⋅K⁻¹⋅mol⁻¹
g₀⋅ft⋅2⁻³3²5⁻⁴ = 0.005380320456000001 [J⋅K⁻¹mol⁻¹]/[lbf⋅ft⋅°R⁻¹lb-mol⁻¹] 英語 -> SI2019
```
