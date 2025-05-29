```Julia
vacuumimpedance(U::UnitSystem) = vacuumpermeability(U)*lightspeed(U)*rationalization(U)*lorentz(U)^2
resistance : [FLTQ⁻²], [FLTQ⁻²], [ML²T⁻¹Q⁻²], [LT⁻¹], [L⁻¹T]
FLTQ⁻² [𝘤⋅μ₀⋅λ⋅αL²] 統一

自由空間の真空インピーダンス `Z₀` は電場と磁場の大きさの比率です (Ω)。

```

Julia julia> vacuumimpedance(Metric) # Ω 𝘤⋅τ⋅2⁻⁶5⁻⁷ = 376.7303134617706 [Ω] Metric

julia> vacuumimpedance(Conventional) # Ω α⋅RK90⋅2 = 376.730306964(58) [Ω] Conventional

julia> vacuumimpedance(CODATA) # Ω α⋅RK⋅2 = 376.73031361(10) [Ω] CODATA

julia> vacuumimpedance(SI2019) # Ω 𝘩⋅𝘦⁻²α⋅2 = 376.730313667(58) [Ω] SI2019

julia> vacuumimpedance(International) # Ω 𝘤⋅Ωᵢₜ⁻¹τ⋅2⁻⁶5⁻⁷ = 376.5439242192821 [Ω] International

julia> vacuumimpedance(InternationalMean) # Ω 𝘤⋅τ⋅2⁻⁶5⁻⁷/1.00049 = 376.5458060168223 [Ω] InternationalMean

julia> 120π # 3e8*μ₀ # Ω 376.99111843077515

julia> vacuumimpedance(EMU) # abΩ 𝘤⋅τ⋅2³5² = 3.767303134617706×10¹¹ [cm⋅s⁻¹] EMU

julia> vacuumimpedance(ESU) # statΩ 𝘤⁻¹τ⋅2⁻¹5⁻² = 4.1916900439033643×10⁻¹⁰ [cm⁻¹s] ESU

julia> vacuumimpedance(HLU) # hlΩ 𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [cm⁻¹s] LorentzHeaviside

julia> vacuumimpedance(IPS) # in⋅lb⋅s⋅C⁻² 𝘤⋅g₀⁻¹ft⁻¹lb⁻¹τ⋅2⁻⁴3⋅5⁻⁷ = 3334.344236337137 [lb⋅in⋅s⋅C⁻²] IPS ```
