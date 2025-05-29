```Julia
magneticpotential : [T⁻¹QRC⁻¹], [T⁻¹Q], [T⁻¹Q], [M¹ᐟ²L¹ᐟ²T⁻¹], [M¹ᐟ²L³ᐟ²T⁻²]
magneticpotential(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)*reluctance(U,S)
magneticpotential(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticpotential(U,S)
T⁻¹QRC⁻¹ [ħ⁻¹ᐟ²𝘄³ᐟ²μ₀⁻¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ¹ᐟ²g₀⁻¹] 統一

```

磁気動力または `magneticpotential` (A, Gb)、単位換算係数。

```Julia
julia> magneticpotential(EMU,Metric) # A⋅Gb⁻¹
τ⁻¹5 = 0.7957747154594768 [C]/[g¹ᐟ²cm¹ᐟ²] EMU -> Metric

julia> magneticpotential(Metric,SI2019) # A⋅A⁻¹
𝘩⁻¹ᐟ²𝘄¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019
```
