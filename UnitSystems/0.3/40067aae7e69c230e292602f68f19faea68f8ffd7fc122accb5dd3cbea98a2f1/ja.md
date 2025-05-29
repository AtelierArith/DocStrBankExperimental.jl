```Julia
photonradiance(U::UnitSystem,S::UnitSystem) = photonirradiance(U,S)/solidangle(U,S)
photonradiance(v::Real,U::UnitSystem,S::UnitSystem) = v/photonradiance(U,S)
```

光子放射率または `photonirradiance` を `solidangle` で割ったもの (Hz⋅m⁻², m⁻²⋅s⁻¹)、単位変換係数。

```Julia
julia> photonradiance(CGS,Metric) # cm²⋅m⁻²
9999.999999999998

julia> photonradiance(English,Metric) # ft²⋅m⁻²
10.76391041670972
```
