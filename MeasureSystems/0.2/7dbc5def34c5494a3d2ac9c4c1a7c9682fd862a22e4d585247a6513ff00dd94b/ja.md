```Julia
angularwavenumber : [L⁻¹A], [L⁻¹], [L⁻¹], [L⁻¹], [L⁻¹]
angularwavenumber(U::UnitSystem,S::UnitSystem) = angle(U,S)/length(U,S)
angularwavenumber(v::Real,U::UnitSystem,S::UnitSystem) = v/angularwavenumber(U,S)
L⁻¹A [ħ⁻¹𝘤⋅mₑ⋅g₀⁻¹] 統一

空間あたりの発生数 (m⁻¹)、単位換算係数。

```

Julia julia> angularwavenumber(CGS,Metric) # cm⋅m⁻¹ 2²5² = 100.0 [m⁻¹]/[cm⁻¹] ガウス -> メトリック

julia> angularwavenumber(English,Metric) # ft⋅m⁻¹ ft⁻¹ = 3.280839895013123 [m⁻¹]/[ft⁻¹] 英語 -> メトリック ```
