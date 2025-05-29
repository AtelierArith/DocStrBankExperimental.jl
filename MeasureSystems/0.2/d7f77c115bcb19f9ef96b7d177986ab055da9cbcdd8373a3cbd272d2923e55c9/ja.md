```Julia
kayser(U::UnitSystem) = wavenumber(𝟏,U,Gauss)
wavenumber : [L⁻¹], [L⁻¹], [L⁻¹], [L⁻¹], [L⁻¹]
L⁻¹⋅(R∞⁻¹α²τ⁻¹2⋅5² = 3.8615926796(12) × 10⁻¹¹) [ħ⁻¹𝘤⋅mₑ⋅ϕ⁻¹g₀⁻¹] 統一

Metric unit of `wavenumber` or curvature (m⁻¹ or ft⁻¹).

```

Julia julia> kayser(Metric) # m⁻¹ 2²5² = 100.0 [m⁻¹] メトリック

julia> kayser(CGS) # cm⁻¹ 𝟏 = 1.0 [cm⁻¹] ガウス

julia> kayser(English) # ft⁻¹ ft⋅2²5² = 30.48 [ft⁻¹] 英語 ```
