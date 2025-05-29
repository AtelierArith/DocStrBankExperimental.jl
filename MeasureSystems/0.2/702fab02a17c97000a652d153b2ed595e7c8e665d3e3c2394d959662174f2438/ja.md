```Julia
diffusionflux : [L⁻²TN], [L⁻²TN], [L⁻²TN], [L⁻²TN], [L⁻²TN]
diffusionflux(U::UnitSystem,S::UnitSystem) = molaramount(U,S)*photonirradiance(U,S)
diffusionflux(v::Real,U::UnitSystem,S::UnitSystem) = v/diffusionflux(U,S)
L⁻²TN [ħ⁻¹mₑ²Mᵤ⁻¹ϕ⁻¹g₀⁻¹] 統一

モル拡散フラックスまたは `molarmount` と `flux` (mol⋅s⁻¹⋅m⁻²)、単位換算係数。

```

Julia julia> diffusionflux(CGS,Metric) # cm²⋅m⁻² 2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] ガウス -> メトリック

julia> diffusionflux(English,Metric) # ft²⋅mol⋅lb-mol⁻¹⋅m⁻² ft⁻²lb⋅2³5³ = 4882.42763638305 [m⁻²mol]/[ft⁻²lb-mol] 英語 -> メトリック ```
