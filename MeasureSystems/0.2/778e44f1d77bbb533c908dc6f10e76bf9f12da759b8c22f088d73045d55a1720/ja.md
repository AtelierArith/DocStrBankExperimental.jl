```Julia
magneton(U::UnitSystem) = elementarycharge(U)*planckreduced(U)*lorentz(U)/2electronmass(U)
nonstandard : [FM⁻¹LTQA⁻¹C⁻¹], [L²T⁻¹Q], [L²T⁻¹Q], [M¹ᐟ²L⁵ᐟ²T⁻¹], [M¹ᐟ²L⁷ᐟ²T⁻²]
FM⁻¹LTQA⁻¹C⁻¹⋅(α¹ᐟ²τ¹ᐟ²2⁻¹ᐟ² = 0.151411060436(12)) [ħ³ᐟ²𝘃⁻¹ᐟ²μ₀⁻¹ᐟ²mₑ⁻¹ϕ¹ᐟ²λ⁻¹ᐟ²] 統一

```

ボーア磁子 `μB` は電子の磁気モーメントを表現するための自然単位 (J⋅T⁻¹) です。

```Julia
julia> magneton(SI2019) # J⋅T⁻¹
𝘤⋅𝘦⋅R∞⁻¹α²τ⁻¹2⁻² = 9.2740100783(28) × 10⁻²⁴ [J⋅T⁻¹] SI2019

julia> magneton(Metric) # J⋅T⁻¹
𝘩¹ᐟ²𝘤¹ᐟ²R∞⁻¹α⁵ᐟ²τ⁻³ᐟ²2³ᐟ²5⁷ᐟ² = 9.2740100808(36) × 10⁻²⁴ [J⋅T⁻¹] Metric

julia> magneton(CODATA) # J⋅T⁻¹
𝘤⋅R∞⁻¹α²RK⁻¹KJ⁻¹τ⁻¹2⁻¹ = 9.274010001(58) × 10⁻²⁴ [J⋅T⁻¹] CODATA

julia> magneton(Conventional) # J⋅T⁻¹
𝘤⋅R∞⁻¹α²RK90⁻¹KJ90⁻¹τ⁻¹2⁻¹ = 9.2740092541(28) × 10⁻²⁴ [J⋅T⁻¹] Conventional

julia> magneton(International) # J⋅T⁻¹
𝘩¹ᐟ²𝘤¹ᐟ²R∞⁻¹α⁵ᐟ²Ωᵢₜ⋅Vᵢₜ⁻¹τ⁻³ᐟ²2³ᐟ²5⁷ᐟ² = 9.2755397877(36) × 10⁻²⁴ [J⋅T⁻¹] International

julia> magneton(ESU) # statA⋅cm²
𝘩¹ᐟ²𝘤³ᐟ²R∞⁻¹α⁵ᐟ²τ⁻³ᐟ²2¹³ᐟ²5¹⁷ᐟ² = 2.7802782776(11) × 10⁻¹⁰ [g¹ᐟ²cm⁷ᐟ²s⁻²] ESU

julia> magneton(SI2019)/elementarycharge(SI2019) # eV⋅T⁻¹
𝘤⋅R∞⁻¹α²τ⁻¹2⁻² = 5.7883818060(18) × 10⁻⁵ [m²s⁻¹] SI2019

julia> magneton(Hartree) # 𝘤⋅ħ⋅mₑ⁻¹
2⁻¹ = 0.5 [𝘦] Hartree
```
