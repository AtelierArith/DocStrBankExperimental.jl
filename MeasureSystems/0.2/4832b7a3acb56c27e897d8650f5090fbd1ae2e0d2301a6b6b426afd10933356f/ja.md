```Julia
currentdensity : [L⁻²T⁻¹Q], [L⁻²T⁻¹Q], [L⁻²T⁻¹Q], [M¹ᐟ²L⁻³ᐟ²T⁻¹], [M¹ᐟ²L⁻¹ᐟ²T⁻²]
currentdensity(U::UnitSystem,S::UnitSystem) = current(U,S)/area(U,S)
currentdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/currentdensity(U,S)
L⁻²T⁻¹Q [ħ⁻⁵ᐟ²𝘤⁷ᐟ²μ₀⁻¹ᐟ²mₑ³ϕ⁻⁵ᐟ²λ⁻¹ᐟ²αL⁻¹g₀⁻³] 統一

断面 `currentdensity` または `current` あたり `area` (A⋅m⁻²)、単位換算係数。

```

Julia julia> currentdensity(EMU,Metric) # A⋅cm²⋅Bi⁻¹⋅m⁻² 2⁵5⁵ = 100000.0 [m⁻²C]/[g¹ᐟ²cm⁻³ᐟ²] EMU -> Metric

julia> currentdensity(ESU,Metric) # A⋅cm²⋅statA⁻¹⋅m⁼² 𝘤⁻¹2³5³ = 3.3356409519815205×10⁻⁶ [m⁻²C]/[g¹ᐟ²cm⁻¹ᐟ²s⁻¹] ESU -> Metric

julia> currentdensity(Metric,SI2019) # A⋅A⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019 ```
