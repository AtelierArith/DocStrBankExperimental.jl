```Julia
bubnoff(U::UnitSystem) = meter(U)/year(U)
```

侵食の基準単位 `speed` (m⋅s⁻¹ または ft⋅s⁻¹)。

```Julia
julia> bubnoff(CGS) # cm⋅s⁻¹
3.1688087814028946e-6

julia> bubnoff(English) # ft⋅s⁻¹
1.0396354269694536e-7
```
