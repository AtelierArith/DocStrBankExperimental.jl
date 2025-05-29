```Julia
electronmass(U::UnitSystem) = protonmass(U)/protonelectron(U) # αinv^2*R∞*2𝘩/𝘤
mass : [M], [FL⁻¹T²], [M], [M], [M]
M [mₑ] 統一

電子の静止質量 `mₑ` は、`-𝘦` の基本電荷を持つ亜原子粒子の質量 (kg またはスラグ)。

```

Julia julia> electronmass(Metric) # kg 𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] Metric

julia> electronmass(CODATA) # kg 𝘃⁻¹R∞⋅α⁻²RK⁻¹KJ⁻²2³ = 9.10938355(11) × 10⁻³¹ [kg] CODATA

julia> electronmass(Conventional) # kg 𝘃⁻¹R∞⋅α⁻²RK90⁻¹KJ90⁻²2³ = 9.1093819203(28) × 10⁻³¹ [kg] Conventional

julia> electronmass(International) # kg 𝘩⋅𝘤⁻¹R∞⋅α⁻²Ωᵢₜ⋅Vᵢₜ⁻²2 = 9.1078806534(28) × 10⁻³¹ [kg] International

julia> electronmass(Metric)/dalton(Metric) # Da μₑᵤ = 0.000548579909065(16) [𝟙] Metric

julia> electronmass(QCD) # mₚ μₑᵤ⋅μₚᵤ⁻¹ = 0.000544617021487(33) [mₚ] QCD

julia> electronmass(Hartree) # mₑ 𝟏 = 1.0 [𝟙] Hartree

julia> electronmass(Metric)*lightspeed(Metric)^2 # J 𝘩⋅𝘤⋅R∞⋅α⁻²2 = 8.1871057769(25) × 10⁻¹⁴ [J] Metric

julia> electronmass(SI2019)*lightspeed(SI2019)^2/elementarycharge(SI2019) # eV⋅𝘤⁻² 𝘩⋅𝘤⋅𝘦⁻¹R∞⋅α⁻²2 = 510998.95000(16) [V] SI2019

julia> electronmass(English) # lb 𝘩⋅𝘤⁻¹R∞⋅α⁻²lb⁻¹2 = 2.00827533796(62) × 10⁻³⁰ [lbm] English ```
