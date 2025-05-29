```Julia
magneticfluxquantum(U::UnitSystem) = planck(U)/𝟐/elementarycharge(U)/lorentz(U)
magneticflux : [FLTQ⁻¹C], [FLTQ⁻¹], [ML²T⁻¹Q⁻¹], [M¹ᐟ²L³ᐟ²T⁻¹], [M¹ᐟ²L¹ᐟ²]
FLTQ⁻¹C⋅(α⁻¹ᐟ²τ¹ᐟ²2⁻³ᐟ² = 10.374382969600(79)) [ħ¹ᐟ²𝘤¹ᐟ²μ₀¹ᐟ²ϕ¹ᐟ²λ¹ᐟ²] 統一

磁束量 `Φ₀` は `𝟏/josephson(U)` (Wb) です。

```

Julia julia> magneticfluxquantum(SI2019) # Wb 𝘩⋅𝘦⁻¹2⁻¹ = 2.0678338484619295×10⁻¹⁵ [Wb] SI2019

julia> magneticfluxquantum(Metric) # Wb 𝘩¹ᐟ²𝘤¹ᐟ²α⁻¹ᐟ²τ¹ᐟ²2⁻⁹ᐟ²5⁻⁷ᐟ² = 2.06783384790(16) × 10⁻¹⁵ [Wb] Metric

julia> magneticfluxquantum(Conventional) # Wb KJ90⁻¹ = 2.0678336278962334×10⁻¹⁵ [Wb] Conventional

julia> magneticfluxquantum(International) # Wb 𝘩¹ᐟ²𝘤¹ᐟ²α⁻¹ᐟ²Vᵢₜ⁻¹τ¹ᐟ²2⁻⁹ᐟ²5⁻⁷ᐟ² = 2.06715168784(16) × 10⁻¹⁵ [Wb] International

julia> magneticfluxquantum(InternationalMean) # Wb 𝘩¹ᐟ²𝘤¹ᐟ²α⁻¹ᐟ²τ¹ᐟ²2⁻⁹ᐟ²5⁻⁷ᐟ²/1.00034 = 2.06713102335(16) × 10⁻¹⁵ [Wb] InternationalMean

julia> magneticfluxquantum(EMU) # Mx 𝘩¹ᐟ²𝘤¹ᐟ²α⁻¹ᐟ²τ¹ᐟ²2⁷ᐟ²5⁹ᐟ² = 2.06783384790(16) × 10⁻⁷ [Mx] EMU

julia> magneticfluxquantum(ESU) # statWb 𝘩¹ᐟ²𝘤⁻¹ᐟ²α⁻¹ᐟ²τ¹ᐟ²2³ᐟ²5⁵ᐟ² = 6.89755126494(53) × 10⁻¹⁸ [g¹ᐟ²cm¹ᐟ²] ESU ```
