```Julia
hartree(U::UnitSystem) = electronmass(U)/gravity(U)*(lightspeed(U)*finestructure(U))^2
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(α² = 5.3251354520(16) × 10⁻⁵) [𝘤²mₑ⋅g₀⁻¹] 統一

水素原子の基底状態におけるハートリー電位エネルギー `Eₕ` は `2R∞*𝘩*𝘤` (J) です。

```

Julia julia> hartree(SI2019)/elementarycharge(SI2019) # eV 𝘩⋅𝘤⋅𝘦⁻¹R∞⋅2 = 27.211386245989(52) [V] SI2019

julia> hartree(Metric) # J 𝘩⋅𝘤⋅R∞⋅2 = 4.3597447222072(83) × 10⁻¹⁸ [J] Metric

julia> hartree(CGS) # erg 𝘩⋅𝘤⋅R∞⋅2⁸5⁷ = 4.3597447222072(83) × 10⁻¹¹ [erg] Gauss

julia> hartree(Metric)*avogadro(Metric)/kilo # kJ⋅mol⁻¹ 𝘤²α²μₑᵤ⋅2⁻⁶5⁻⁶ = 2625.49964038(81) [J⋅mol⁻¹] Metric

julia> hartree(Metric)*avogadro(Metric)/kilocalorie(Metric) # kcal⋅mol⁻¹ 𝘤²α²μₑᵤ⋅Ωᵢₜ⋅Vᵢₜ⁻²2⁻⁸3⁻²5⁻⁷43 = 627.09920344(19) [mol⁻¹] Metric

julia> 𝟐*rydberg(CGS) # Eₕ/𝘩/𝘤/100 cm⁻¹ R∞⋅2⁻¹5⁻² = 219474.63136320(42) [cm⁻¹] Gauss

julia> hartree(Metric)/planck(Metric) # Hz 𝘤⋅R∞⋅2 = 6.579683920502(13) × 10¹⁵ [Hz] Metric

julia> hartree(Metric)/boltzmann(Metric) # K kB⁻¹NA⁻¹𝘤²α²μₑᵤ⋅2⁻³5⁻³ = 315775.024913(97) [K] Metric ```

ガウス単位系では `4π*ε₀ == 1` のとき、ハートリーエネルギーは `𝘦^2/a₀` です。
