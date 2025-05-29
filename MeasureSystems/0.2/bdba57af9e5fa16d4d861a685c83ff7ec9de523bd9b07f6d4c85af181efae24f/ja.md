```Julia
luminousexposure : [L⁻²TJ], [L⁻²TJ], [L⁻²TJ], [L⁻²TJ], [L⁻²TJ]
luminousexposure(U::UnitSystem,S::UnitSystem) = illuminance(U,S)*time(U,S)
luminousexposure(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousexposure(U,S)
L⁻²TJ [ħ⁻²𝘤⁴mₑ³Kcd⋅ϕ⁻²g₀⁻³] 統一

時間に沿った `luminance` の統合 (lx⋅s, lm⋅s⋅m⁻², cd⋅s⋅m⁻²⋅sr)、単位変換係数。

```

Julia julia> luminousexposure(CGS,Metric) # lx⋅ph⁻¹ 2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] ガウス -> メトリック

julia> luminousexposure(IAU,Metric) # s⋅au²⋅day⁻¹⋅m⁻² au⁻²2⁷3³5² = 3.86067211159(15) × 10⁻¹⁸ [Hz⋅m⁻²]/[au⁻²D] IAU☉ -> メトリック

julia> luminousexposure(English,Metric) # ft²⋅m⁻² ft⁻² = 10.76391041670972 [m⁻²]/[ft⁻²] 英語 -> メトリック ```
