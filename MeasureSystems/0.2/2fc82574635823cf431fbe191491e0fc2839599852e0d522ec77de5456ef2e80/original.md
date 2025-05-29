```Julia
eddington(U::UnitSystem) = mass(𝟏,U,Cosmological)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻²𝘤³R∞⁻¹α²ΩΛ⁻¹ᐟ²H0⁻¹au⋅mP²τ⁻¹ᐟ²2⁸3⁷ᐟ²5⁶ = 2.804(21) × 10⁸²) [mₑ] Unified
```

Approximate number of protons in the `Universe` as estimated by Eddington (kg or lb).

```Julia
julia> 𝟐^2^2^3/α # mₚ
α⁻¹2²⁵⁶ = 1.58676846347(24) × 10⁷⁹

julia> eddington(QCD) # mₚ
𝘩⁻²𝘤³R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹ΩΛ⁻¹ᐟ²H0⁻¹au⋅mP²τ⁻¹ᐟ²2⁸3⁷ᐟ²5⁶ = 1.527(11) × 10⁷⁹ [mₚ] QCD

julia> eddington(Metric) # kg
𝘩⁻¹𝘤²ΩΛ⁻¹ᐟ²H0⁻¹au⋅mP²τ⁻¹ᐟ²2⁹3⁷ᐟ²5⁶ = 2.555(19) × 10⁵² [kg] Metric

julia> eddington(IAU) # M☉
𝘤³ΩΛ⁻¹ᐟ²H0⁻¹au⁻²kG⁻²τ⁻⁷ᐟ²2³⁷3³⁵ᐟ²5¹⁶ = 1.2847(95) × 10²² [M☉] IAU☉

julia> eddington(Cosmological)
𝟏 = 1.0 [M] Cosmological
```
