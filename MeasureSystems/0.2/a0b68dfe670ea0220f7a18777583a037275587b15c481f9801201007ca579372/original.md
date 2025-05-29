```Julia
specificmagnetization : [F⁻¹ML⁻²T⁻¹QC⁻¹], [L⁻³TQ], [L⁻³TQ], [M¹ᐟ²L⁻⁵ᐟ²T], [M¹ᐟ²L⁻³ᐟ²]
specificmagnetization(U::UnitSystem,S::UnitSystem) = magneticmoment(U,S)/mass(U,S)
specificmagnetization(v::Real,U::UnitSystem,S::UnitSystem) = v/specificmagnetization(U,S)
F⁻¹ML⁻²T⁻¹QC⁻¹ [ħ⁻³ᐟ²𝘤¹ᐟ²μ₀⁻¹ᐟ²mₑ²ϕ⁻³ᐟ²λ⁻¹ᐟ²g₀⁻¹] Unified
```

Amount of `magneticmoment` per `mass` (Wb⋅m⋅kg⁻¹), unit conversion factor.

```Julia
julia> specificmagnetization(EMU,Metric) # Wb⋅m⋅g⋅Mx⁻¹⋅cm⁻¹⋅kg⁻¹
2⁷5⁷ = 1.0×10⁷ [m⁻³s²C]/[g¹ᐟ²cm⁻⁵ᐟ²s²] EMU -> Metric

julia> specificmagnetization(ESU,Metric) # Wb⋅m⋅g⋅statWb⁻¹⋅cm⁻¹⋅kg⁻¹
𝘤⁻¹2⁵5⁵ = 0.00033356409519815205 [m⁻³s²C]/[g¹ᐟ²cm⁻³ᐟ²s] ESU -> Metric

julia> specificmagnetization(Metric,SI2019) # Wb⋅Wb⁻¹
𝘩⁻¹ᐟ²𝘤¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019
```
