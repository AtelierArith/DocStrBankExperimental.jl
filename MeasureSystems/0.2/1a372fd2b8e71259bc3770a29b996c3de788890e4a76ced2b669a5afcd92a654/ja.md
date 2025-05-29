```Julia
faraday(U::UnitSystem) = elementarycharge(U)*avogadro(U)
nonstandard : [QN⁻¹], [QN⁻¹], [QN⁻¹], [M¹ᐟ²L¹ᐟ²N⁻¹], [M¹ᐟ²L³ᐟ²T⁻¹N⁻¹]
QN⁻¹⋅(α¹ᐟ²μₑᵤ⋅τ¹ᐟ²2¹ᐟ² = 0.000166122131531(14)) [ħ¹ᐟ²𝘤⁻¹ᐟ²μ₀⁻¹ᐟ²mₑ⁻¹Mᵤ⋅ϕ¹ᐟ²λ⁻¹ᐟ²αL⁻¹] 統一

電荷モルあたりの電子 `𝔉` は基本電荷に基づいています (C⋅mol⁻¹)。

```

Julia julia> faraday(SI2019) # C⋅mol⁻¹ NA⋅𝘦 = 96485.33212331001 [C⋅mol⁻¹] SI2019

julia> faraday(Metric) # C⋅mol⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²R∞⁻¹α⁵ᐟ²μₑᵤ⋅τ⁻¹ᐟ²2⁻¹ᐟ²5¹ᐟ² = 96485.332183(37) [C⋅mol⁻¹] Metric

julia> faraday(CODATA) # C⋅mol⁻¹ 𝘤⋅R∞⁻¹α²μₑᵤ⋅KJ⋅2⁻⁵5⁻³ = 96485.33297(60) [C⋅mol⁻¹] CODATA

julia> faraday(Conventional) # C⋅mol⁻¹ 𝘤⋅R∞⁻¹α²μₑᵤ⋅KJ90⋅2⁻⁵5⁻³ = 96485.342448(30) [C⋅mol⁻¹] Conventional

julia> faraday(International) # C⋅mol⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²R∞⁻¹α⁵ᐟ²μₑᵤ⋅Ωᵢₜ⋅Vᵢₜ⁻¹τ⁻¹ᐟ²2⁻¹ᐟ²5¹ᐟ² = 96501.247011(37) [C⋅mol⁻¹] International

julia> faraday(InternationalMean) # C⋅mol⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²R∞⁻¹α⁵ᐟ²μₑᵤ⋅τ⁻¹ᐟ²2⁻¹ᐟ²5¹ᐟ²⋅1.0001499490173342 = 96499.800064(37) [C⋅mol⁻¹] InternationalMean

julia> faraday(EMU) # abC⋅mol⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²R∞⁻¹α⁵ᐟ²μₑᵤ⋅τ⁻¹ᐟ²2⁻³ᐟ²5⁻¹ᐟ² = 9648.5332183(37) [g¹ᐟ²cm¹ᐟ²mol⁻¹] EMU

julia> faraday(ESU) # statC⋅mol⁻¹ 𝘩⁻¹ᐟ²𝘤³ᐟ²R∞⁻¹α⁵ᐟ²μₑᵤ⋅τ⁻¹ᐟ²2¹ᐟ²5³ᐟ² = 2.8925574896(11) × 10¹⁴ [g¹ᐟ²cm³ᐟ²s⁻¹mol⁻¹] ESU

julia> faraday(Metric)/kilocalorie(Metric) # kcal⋅(V-g-e)⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²R∞⁻¹α⁵ᐟ²μₑᵤ⋅Ωᵢₜ⋅Vᵢₜ⁻²τ⁻¹ᐟ²2⁻¹¹ᐟ²3⁻²5⁻⁷ᐟ²43 = 23.0454706695(89) [kg⁻¹m⁻²s²C⋅mol⁻¹] Metric

julia> faraday(Metric)/3600 # A⋅h⋅mol⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²R∞⁻¹α⁵ᐟ²μₑᵤ⋅τ⁻¹ᐟ²2⁻⁹ᐟ²3⁻²5⁻³ᐟ² = 26.801481162(10) [C⋅mol⁻¹] Metric ```
