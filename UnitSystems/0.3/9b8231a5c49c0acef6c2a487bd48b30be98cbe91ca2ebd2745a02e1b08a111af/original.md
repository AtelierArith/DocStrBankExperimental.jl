```Julia
photonintensity(U::UnitSystem,S::UnitSystem) = frequency(U,S)/solidangle(U,S)
photonintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/photonintensity(U,S)
```

Photon intensity or `frequency` per `area` (Hz⋅m⁻², m⁻²⋅s⁻¹), unit conversion factor.

```Julia
julia> photonintensity(IAU,Metric) day⋅s⁻¹
1.1574074074074073e-5
```
