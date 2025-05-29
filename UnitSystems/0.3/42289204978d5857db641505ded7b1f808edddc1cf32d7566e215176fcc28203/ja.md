```Julia
photonirradiance(U::UnitSystem,S::UnitSystem) = 1/area(U,S)/time(U,S)
photonirradiance(v::Real,U::UnitSystem,S::UnitSystem) = v/photonirradiance(U,S)
```

面積あたりの光子フラックスまたは `frequency` (Hz⋅m⁻², m⁻²⋅s⁻¹)、単位変換係数。

```Julia
julia> photonirradiance(CGS,Metric) # cm²⋅m⁻²
9999.999999999998

julia> photonirradiance(English,Metric) # ft²⋅m⁻²
10.76391041670972
```
