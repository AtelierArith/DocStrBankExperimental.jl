```Julia
gravitation(U::UnitSystem) = lightspeed(U)*planckreduced(U)/planckmass(U)^2
nonstandard : [FM⁻²L²], [F⁻¹L⁴T⁻⁴], [M⁻¹L³T⁻²], [M⁻¹L³T⁻²], [M⁻¹L³T⁻²]
FM⁻²L²⋅(𝘩²𝘤⁻²R∞²α⁻⁴mP⁻²2² = 1.751810(39) × 10⁻⁴⁵) [ħ⋅𝘤⋅mₑ⁻²ϕ] Unified
```

Universal gravitational constant `G` of Newton's law (m³⋅kg⁻¹⋅s⁻² or ft³⋅slug⁻¹⋅s⁻²).

```Julia
juila> gravitation(Metric) # m³⋅kg⁻¹⋅s⁻²
𝘩⋅𝘤⋅mP⁻²τ⁻¹ = 6.67430(15) × 10⁻¹¹ [kg⁻¹m³s⁻²] Metric

julia> gravitation(English) # ft³⋅lbm⁻¹⋅s⁻²
𝘩⋅𝘤⋅g₀⁻¹ft⁻²lb⋅mP⁻²τ⁻¹ = 3.322929(73) × 10⁻¹¹ [lbf⋅lbm⁻²ft²] English

julia> gravitation(PlanckGauss)
𝟏 = 1.0 [mP⁻²] PlanckGauss
```
