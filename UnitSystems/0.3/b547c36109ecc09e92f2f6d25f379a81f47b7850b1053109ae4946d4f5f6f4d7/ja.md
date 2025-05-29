```Julia
rayleigh(U::UnitSystem) = photonirradiance(𝟏𝟎^10,U,Metric)
```

`photonirradiance` の一般的な単位 (Hz⋅m⁻²)。

```Julia
julia> rayleigh(Metric) # Hz⋅m⁻²
1.0e10

julia> rayleigh(CGS) # Hz⋅cm⁻²
1.0000000000000002e6

julia> rayleigh(English) # Hz⋅ft⁻²
9.290304000000002e8
```
