```Julia
diffusionflux(U::UnitSystem,S::UnitSystem) = molaramount(U,S)*photonirradiance(U,S)
diffusionflux(v::Real,U::UnitSystem,S::UnitSystem) = v/diffusionflux(U,S)
```

モル拡散フラックスまたは `molarmount` と `flux` (mol⋅s⁻¹⋅m⁻²)、単位換算係数。

```Julia
julia> diffusionflux(CGS,Metric) # cm²⋅m⁻²
9999.999999999998

julia> diffusionflux(English,Metric) # ft²⋅mol⋅lb-mol⁻¹⋅m⁻²
4882.4276363830495
```
