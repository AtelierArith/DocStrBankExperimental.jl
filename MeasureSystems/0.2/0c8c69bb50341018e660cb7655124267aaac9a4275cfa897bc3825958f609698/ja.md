```Julia
stagnance : [L⁻¹T], [L⁻¹T], [L⁻¹T], [L⁻¹T], [L⁻¹T]
stagnance(U::UnitSystem,S::UnitSystem) = lightspeed(U)/lightspeed(S)
stagnance(v::Real,U::UnitSystem,S::UnitSystem) = v/stagnance(U,S)
L⁻¹T [𝘤⁻¹] 統一

```

滞留または `時間` あたり `長さ` (s⋅m⁻¹)、単位換算係数。

```Julia
julia> stagnance(CGS,Metric) # cm⋅m⁻¹
2²5² = 100.0 [m⁻¹]/[cm⁻¹] ガウス -> メトリック

julia> stagnance(IAU,Metric) # au⋅s⋅day⁻¹⋅m⁻¹
au⁻¹2⁷3³5² = 5.77548327364(12) × 10⁻⁷ [m⁻¹s]/[au⁻¹D] IAU☉ -> メトリック

julia> stagnance(English,Metric) # ft⋅m⁻¹
ft⁻¹ = 3.280839895013123 [m⁻¹]/[ft⁻¹] 英語 -> メトリック

julia> stagnance(Survey,English) # ftUS⋅ft⁻¹
ft⋅ftUS⁻¹ = 0.9999980000000002 [ft⁻¹]/[ft⁻¹] 調査 -> 英語
```
