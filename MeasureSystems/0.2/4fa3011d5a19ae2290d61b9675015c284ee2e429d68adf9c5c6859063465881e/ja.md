```Julia
photonradiance : [L⁻²TA⁻²], [L⁻²T], [L⁻²T], [L⁻²T], [L⁻²T]
photonradiance(U::UnitSystem,S::UnitSystem) = photonirradiance(U,S)/solidangle(U,S)
photonradiance(v::Real,U::UnitSystem,S::UnitSystem) = v/photonradiance(U,S)
L⁻²TA⁻² [ħ⁻¹mₑ⋅ϕ⁻³g₀⁻¹] 統一

光子放射率または `photonirradiance` を `solidangle` で割ったもの (Hz⋅m⁻², m⁻²⋅s⁻¹)、単位変換係数。

```

Julia julia> photonradiance(CGS,Metric) # cm²⋅m⁻² 2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] ガウス -> メトリック

julia> photonradiance(English,Metric) # ft²⋅m⁻² ft⁻² = 10.76391041670972 [m⁻²]/[ft⁻²] 英語 -> メトリック ```
