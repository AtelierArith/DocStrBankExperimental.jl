```Julia
dalton(U::UnitSystem) = molarmass(U)/avogadro(U)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(μₑᵤ⁻¹ = 1822.888486209(53)) [mₑ] 統一

原子質量単位 `Da` は、C₁₂ 炭素-12 原子の質量の1/12 (kg またはスラグ)。

```

Julia julia> dalton(Metric) # kg 𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2 = 1.66053906660(51) × 10⁻²⁷ [kg] メトリック

julia> dalton(Hartree) # mₑ μₑᵤ⁻¹ = 1822.888486209(53) [𝟙] ハートリー

julia> dalton(QCD) # mₚ μₚᵤ⁻¹ = 0.992776097862(52) [mₚ] QCD

julia> dalton(Metric)*lightspeed(Metric)^2 # J 𝘩⋅𝘤⋅R∞⋅α⁻²μₑᵤ⁻¹2 = 1.49241808560(46) × 10⁻¹⁰ [J] メトリック

julia> dalton(SI2019)*lightspeed(SI2019)^2/elementarycharge(SI2019) # eV⋅𝘤⁻² 𝘩⋅𝘤⋅𝘦⁻¹R∞⋅α⁻²μₑᵤ⁻¹2 = 9.3149410242(29) × 10⁸ [V] SI2019

julia> dalton(British) # lb 𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁻¹ft⋅lb⁻¹2 = 1.13783069118(35) × 10⁻²⁸ [slug] ブリティッシュ ```
