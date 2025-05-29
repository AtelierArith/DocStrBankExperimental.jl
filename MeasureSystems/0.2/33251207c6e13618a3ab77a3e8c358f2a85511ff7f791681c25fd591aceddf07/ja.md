```Julia
klitzing(U::UnitSystem) = planck(U)/elementarycharge(U)^2
resistance : [FLTQ⁻²], [FLTQ⁻²], [ML²T⁻¹Q⁻²], [LT⁻¹], [L⁻¹T]
FLTQ⁻²⋅(α⁻¹2⁻¹ = 68.517999542(10)) [𝘤⋅μ₀⋅λ⋅αL²] 統一

量子ホール抵抗 `RK` (Ω)。

```

Julia julia> klitzing(SI2019) # Ω 𝘩⋅𝘦⁻² = 25812.80745930451 [Ω] SI2019

julia> klitzing(Metric) # Ω 𝘤⋅α⁻¹τ⋅2⁻⁷5⁻⁷ = 25812.8074452(40) [Ω] Metric

julia> klitzing(Conventional) # Ω RK90 = 25812.807 [Ω] Conventional

julia> klitzing(International) # Ω 𝘤⋅α⁻¹Ωᵢₜ⁻¹τ⋅2⁻⁷5⁻⁷ = 25800.036427200(40) [Ω] International

julia> klitzing(CODATA) # Ω RK = 25812.8074555(59) [Ω] CODATA

julia> klitzing(EMU) # abΩ 𝘤⋅α⁻¹τ⋅2²5² = 2.58128074452(40) × 10¹³ [cm⋅s⁻¹] EMU

julia> klitzing(ESU) # statΩ 𝘤⁻¹α⁻¹τ⋅2⁻²5⁻² = 2.87206216508(44) × 10⁻⁸ [cm⁻¹s] ESU ```
