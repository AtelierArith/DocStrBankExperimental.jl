```Julia
josephson(U::UnitSystem) = 𝟐*elementarycharge(U)*lorentz(U)/planck(U)
nonstandard : [F⁻¹L⁻¹T⁻¹QC⁻¹], [F⁻¹L⁻¹T⁻¹Q], [M⁻¹L⁻²TQ], [M⁻¹ᐟ²L⁻³ᐟ²T], [M⁻¹ᐟ²L⁻¹ᐟ²]
F⁻¹L⁻¹T⁻¹QC⁻¹⋅(α¹ᐟ²τ⁻¹ᐟ²2³ᐟ² = 0.0963912748286(74)) [ħ⁻¹ᐟ²𝘤⁻¹ᐟ²μ₀⁻¹ᐟ²ϕ⁻¹ᐟ²λ⁻¹ᐟ²] 統一

ジョセフソン定数 `KJ` は電位差と照射周波数 (Hz⋅V⁻¹) を関連付けます。

```

Julia julia> josephson(SI2019) # Hz⋅V⁻¹ 𝘩⁻¹𝘦⋅2 = 4.8359784841698356×10¹⁴ [Hz⋅V⁻¹] SI2019

julia> josephson(Metric) # Hz⋅V⁻¹ 𝘩⁻¹ᐟ²𝘤⁻¹ᐟ²α¹ᐟ²τ⁻¹ᐟ²2⁹ᐟ²5⁷ᐟ² = 4.83597848549(37) × 10¹⁴ [Hz⋅V⁻¹] Metric

julia> josephson(Conventional) # Hz⋅V⁻¹ KJ90 = 4.835979×10¹⁴ [Hz⋅V⁻¹] Conventional

julia> josephson(CODATA) # Hz⋅V⁻¹ KJ = 4.835978525(30) × 10¹⁴ [Hz⋅V⁻¹] CODATA

julia> josephson(International) # Hz⋅V⁻¹ 𝘩⁻¹ᐟ²𝘤⁻¹ᐟ²α¹ᐟ²Vᵢₜ⋅τ⁻¹ᐟ²2⁹ᐟ²5⁷ᐟ² = 4.83757435839(37) × 10¹⁴ [Hz⋅V⁻¹] International

julia> josephson(EMU) # Hz⋅abV⁻¹ 𝘩⁻¹ᐟ²𝘤⁻¹ᐟ²α¹ᐟ²τ⁻¹ᐟ²2⁻⁷ᐟ²5⁻⁹ᐟ² = 4.83597848549(37) × 10⁶ [g⁻¹ᐟ²cm⁻³ᐟ²s] EMU

julia> josephson(ESU) # Hz⋅statV⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²α¹ᐟ²τ⁻¹ᐟ²2⁻³ᐟ²5⁻⁵ᐟ² = 1.44978987700(11) × 10¹⁷ [g⁻¹ᐟ²cm⁻¹ᐟ²] ESU ```
