```Julia
diopter(U::UnitSystem) = angularwavenumber(𝟏,U,Metric)
angularwavenumber : [L⁻¹A], [L⁻¹], [L⁻¹], [L⁻¹], [L⁻¹]
L⁻¹A⋅(R∞⁻¹α²τ⁻¹2⁻¹ = 3.8615926796(12) × 10⁻¹³) [ħ⁻¹𝘤⋅mₑ⋅g₀⁻¹] 統一

Metric unit of `angularwavenumber` or curvature (m⁻¹ or ft⁻¹).

```

Julia julia> diopter(Metric) # m⁻¹ 𝟏 = 1.0 [m⁻¹] Metric

julia> diopter(CGS) # cm⁻¹ 2⁻²5⁻² = 0.010000000000000002 [cm⁻¹] ガウス

julia> diopter(English) # ft⁻¹ ft = 0.3048 [ft⁻¹rad] 英語 ```
