```Julia
rayleigh(U::UnitSystem) = photonirradiance(𝟏𝟎^10,U,Metric)
```

Common unit of `photonirradiance` (Hz⋅m⁻²).

```Julia
julia> rayleigh(Metric) # Hz⋅m⁻²
1.0e10

julia> rayleigh(CGS) # Hz⋅cm⁻²
1.0000000000000002e6

julia> rayleigh(English) # Hz⋅ft⁻²
9.290304000000002e8
```
