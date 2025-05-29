```Julia
photonintensity(U::UnitSystem,S::UnitSystem) = frequency(U,S)/solidangle(U,S)
photonintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/photonintensity(U,S)
```

光子強度または `frequency` あたりの `area` (Hz⋅m⁻², m⁻²⋅s⁻¹)、単位変換係数。

```Julia
julia> photonintensity(IAU,Metric) day⋅s⁻¹
1.1574074074074073e-5
```
