```Julia
wavenumber : [L⁻¹], [L⁻¹], [L⁻¹], [L⁻¹], [L⁻¹]
wavenumber(U::UnitSystem,S::UnitSystem) = 1/length(U,S)
wavenumber(v::Real,U::UnitSystem,S::UnitSystem) = v/wavenumber(U,S)
L⁻¹ [ħ⁻¹𝘤⋅mₑ⋅ϕ⁻¹g₀⁻¹] 統一

空間の単位あたりの出現数 (m⁻¹)、単位換算係数。

```

Julia julia> wavenumber(CGS,Metric) # cm⋅m⁻¹ 2²5² = 100.0 [m⁻¹]/[cm⁻¹] ガウス -> メトリック

julia> wavenumber(English,Metric) # ft⋅m⁻¹ ft⁻¹ = 3.280839895013123 [m⁻¹]/[ft⁻¹] 英語 -> メトリック ```
