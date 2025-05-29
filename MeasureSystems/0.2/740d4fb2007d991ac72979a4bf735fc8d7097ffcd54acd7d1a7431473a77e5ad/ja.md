```Julia
protonmass(U::UnitSystem) = protonunit(U)*dalton(U)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(μₑᵤ⁻¹μₚᵤ = 1836.15267343(11)) [mₑ] 統一

プロトン質量 `mₚ` は `+𝘦` の素電荷を持つ亜原子粒子の質量 (kg)。

```

Julia julia> protonmass(Metric) # kg 𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹μₚᵤ⋅2 = 1.67262192369(52) × 10⁻²⁷ [kg] メトリック

julia> protonmass(SI2019)*lightspeed(SI2019)^2/elementarycharge(SI2019) # eV⋅𝘤⁻² 𝘩⋅𝘤⋅𝘦⁻¹R∞⋅α⁻²μₑᵤ⁻¹μₚᵤ⋅2 = 9.3827208816(29) × 10⁸ [V] SI2019

julia> protonmass(Metric)/dalton(Metric) # Da μₚᵤ = 1.007276466621(53) [𝟙] メトリック

julia> protonmass(Hartree) # mₑ μₑᵤ⁻¹μₚᵤ = 1836.15267343(11) [𝟙] ハートリー

julia> protonmass(QCD) # mₚ 𝟏 = 1.0 [mₚ] QCD ```
