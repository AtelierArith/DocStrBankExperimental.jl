```Julia
magneticflux : [FLTQ⁻¹C], [FLTQ⁻¹], [ML²T⁻¹Q⁻¹], [M¹ᐟ²L³ᐟ²T⁻¹], [M¹ᐟ²L¹ᐟ²]
magneticflux(U::UnitSystem,S::UnitSystem) = energy(U,S)/lorentz(U,S)/current(U,S)
magneticflux(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticflux(U,S)
FLTQ⁻¹C [ħ¹ᐟ²𝘃¹ᐟ²μ₀¹ᐟ²ϕ¹ᐟ²λ¹ᐟ²] 統一

表面 `magneticflux` または `energy` あたり `current` (Wb, J⋅A⁻¹, V⋅s)、単位換算係数。

```

Julia julia> magneticflux(EMU,Metric) # Wb⋅Mx⁻¹ 2⁻⁸5⁻⁸ = 1.0×10⁻⁸ [V]/[g¹ᐟ²cm³ᐟ²s⁻²] EMU -> Metric

julia> magneticflux(ESU,Metric) # Wb⋅statWb⁻¹ 𝘤⋅2⁻⁶5⁻⁶ = 299.792458 [V]/[g¹ᐟ²cm¹ᐟ²s⁻¹] ESU -> Metric

julia> magneticflux(Metric,SI2019) # Wb⋅Wb⁻¹ 𝘩¹ᐟ²𝘃⁻¹ᐟ²𝘦⁻¹α¹ᐟ²τ⁻¹ᐟ²2⁷ᐟ²5⁷ᐟ² = 1.000000000273(77) [C⁻¹]/[C⁻¹] Metric -> SI2019 ```
