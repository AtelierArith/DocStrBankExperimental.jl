```Julia
numberdensity : [L⁻³], [L⁻³], [L⁻³], [L⁻³], [L⁻³]
numberdensity(U::UnitSystem,S::UnitSystem) = 1/volume(U,S)
numberdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/numberdensity(U,S)
L⁻³ [ħ⁻³𝘤³mₑ³ϕ⁻³g₀⁻³] 統一

体積あたりの数または数密度 (m⁻³ または ft⁻³)、単位換算係数。

```

Julia julia> numberdensity(CGS,Metric) # cm³⋅m⁻³ 2⁶5⁶ = 1.0×10⁶ [m⁻³]/[mL⁻¹] ガウス -> メトリック

julia> numberdensity(English,Metric) # ft³⋅m⁻³ ft⁻³ = 35.314666721488585 [m⁻³]/[ft⁻³] 英語 -> メトリック ```
