```Julia
technicalatmosphere(U::UnitSystem) = kilopond(U)/(centi*meter(U))^2
```

Gravitational Metric unit of `pressure` (Pa or lb⋅ft⁻²).

```Julia
julia> technicalatmosphere(Metric) # Pa
98066.49999999999

julia> technicalatmosphere(English) # lb⋅ft⁻²
2048.161436225217

julia> technicalatmosphere(IPS) # lb⋅in⁻²
14.223343307119565
```
