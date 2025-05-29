```Julia
vectorpotential : [FTQ⁻¹C], [FTQ⁻¹], [MLT⁻¹Q⁻¹], [M¹ᐟ²L¹ᐟ²T⁻¹], [M¹ᐟ²L⁻¹ᐟ²]
vectorpotential(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)/length(U,S)
vectorpotential(v::Real,U::UnitSystem,S::UnitSystem) = v/vectorpotential(U,S)
FTQ⁻¹C [ħ⁻¹ᐟ²𝘄³ᐟ²μ₀¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ¹ᐟ²g₀⁻¹] 統一

磁気 `vectorpotential` または電磁剛性 (Wb⋅m⁻¹ または T⋅m)、単位換算係数。

```

julia julia> vectorpotential(EMU,Metric) # Wb⋅cm⋅Mx⁻¹⋅m⁻¹ 2⁻⁶5⁻⁶ = 1.0×10⁻⁶ [V⋅m⁻¹]/[g¹ᐟ²cm¹ᐟ²s⁻²] EMU -> Metric

julia> vectorpotential(ESU,Metric) # Wb⋅cm⋅statWb⁻¹⋅m⁻¹ 𝘤⋅2⁻⁴5⁻⁴ = 29979.2458 [V⋅m⁻¹]/[g¹ᐟ²cm⁻¹ᐟ²s⁻¹] ESU -> Metric

julia> vectorpotential(Metric,SI2019) # Wb⋅Wb⁻¹ 𝘩¹ᐟ²𝘤⁻¹ᐟ²𝘦⁻¹α¹ᐟ²τ⁻¹ᐟ²2⁷ᐟ²5⁷ᐟ² = 1.000000000273(77) [C⁻¹]/[C⁻¹] Metric -> SI2019 ```
