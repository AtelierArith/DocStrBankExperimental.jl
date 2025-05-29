```Julia
diffusionflux(U::UnitSystem,S::UnitSystem) = molaramount(U,S)*photonirradiance(U,S)
diffusionflux(v::Real,U::UnitSystem,S::UnitSystem) = v/diffusionflux(U,S)
```

Molar diffusion flux or `molarmount` times `flux` (mol⋅s⁻¹⋅m⁻²), unit conversion factor.

```Julia
julia> diffusionflux(CGS,Metric) # cm²⋅m⁻²
9999.999999999998

julia> diffusionflux(English,Metric) # ft²⋅mol⋅lb-mol⁻¹⋅m⁻²
4882.4276363830495
```
