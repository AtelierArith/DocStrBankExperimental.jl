```Julia
photonirradiance : [L⁻²T], [L⁻²T], [L⁻²T], [L⁻²T], [L⁻²T]
photonirradiance(U::UnitSystem,S::UnitSystem) = 1/area(U,S)/time(U,S)
photonirradiance(v::Real,U::UnitSystem,S::UnitSystem) = v/photonirradiance(U,S)
L⁻²T [ħ⁻¹mₑ⋅ϕ⁻¹g₀⁻¹] 統一

光子フラックスまたは `周波数` あたりの `面積` (Hz⋅m⁻², m⁻²⋅s⁻¹)、単位変換係数。

```

Julia julia> photonirradiance(CGS,Metric) # cm²⋅m⁻² 2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] ガウス -> メトリック

julia> photonirradiance(English,Metric) # ft²⋅m⁻² ft⁻² = 10.76391041670972 [m⁻²]/[ft⁻²] 英語 -> メトリック ```
