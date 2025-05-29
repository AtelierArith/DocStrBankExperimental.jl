```Julia
planckmass(U::UnitSystem) = electronmass(U)/sqrt(coupling(U))
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²mP⋅2⁻¹ = 2.389222(26) × 10²²) [mₑ] 統一

Planck mass factor `mP` from the gravitational coupling constant `αG` (kg or slugs).

```

Julia juila> planckmass(Metric)*lightspeed(Metric)^2/elementarycharge(Metric) # eV⋅𝘤⁻² 𝘩⁻¹ᐟ²𝘤⁵ᐟ²α⁻¹ᐟ²mP⋅τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 1.220890(13) × 10²⁸ [V] メトリック

juila> planckmass(Metric) # kg mP = 2.176434(24) × 10⁻⁸ [kg] メトリック

juila> planckmass(Metric)/dalton(Metric) # Da 𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅mP⋅2⁻¹ = 1.310679(14) × 10¹⁹ [𝟙] メトリック

juila> planckmass(Metric)*lightspeed(Metric)^2/elementarycharge(Metric)/sqrt(𝟐^2*τ) # eV⋅𝘤⁻² 𝘩⁻¹ᐟ²𝘤⁵ᐟ²α⁻¹ᐟ²mP⋅2⁻⁹ᐟ²5⁻⁷ᐟ² = 2.435323(27) × 10²⁷ [V] メトリック

julia> planckmass(PlanckGauss) # mP 𝟏 = 1.0 [mP] プランクガウス ```
