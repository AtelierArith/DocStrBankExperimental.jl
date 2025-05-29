```Julia
solarflux(U::UnitSystem) = hecto^2*jansky(U)
```

Reference unit of spectral irradiance (kg⋅s⁻² or lb⋅ft⁻¹).

```Julia
julia> solarflux(Metric) # kg⋅s⁻²
1.0000000000000015e-22

julia> solarflux(CGS) # g⋅s⁻²
1.0000000000000019e-19

julia> solarflux(English) # lb⋅ft⁻¹
6.852176585679186e-24
```
