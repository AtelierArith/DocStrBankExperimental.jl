```Julia
polestrength : [LT⁻¹QA⁻¹C⁻¹], [LT⁻¹Q], [LT⁻¹Q], [M¹ᐟ²L³ᐟ²T⁻¹], [M¹ᐟ²L⁵ᐟ²T⁻²]
polestrength(U::UnitSystem,S::UnitSystem) = magneticdipolemoment(U,S)/length(U,S)
polestrength(v::Real,U::UnitSystem,S::UnitSystem) = v/polestrength(U,S)
LT⁻¹QA⁻¹C⁻¹ [ħ¹ᐟ²𝘤¹ᐟ²μ₀⁻¹ᐟ²ϕ⁻¹ᐟ²λ⁻¹ᐟ²] 統一

```

磁気 `polestrength` は `charge` (A⋅m) に類似しており、単位変換係数です。

```Julia
julia> polestrength(EMU,Metric) # A⋅m⋅pole⁻¹
2⁻¹5⁻¹ = 0.1 [m⋅C]/[g¹ᐟ²cm³ᐟ²] EMU -> Metric

julia> polestrength(Metric,SI2019) # A⋅A⁻¹⋅
𝘩⁻¹ᐟ²𝘤¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019
```
