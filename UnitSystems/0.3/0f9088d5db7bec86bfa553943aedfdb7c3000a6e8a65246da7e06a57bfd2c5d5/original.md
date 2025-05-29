```Julia
fps(U::UnitSystem) = feet(U)/second(U)
```

Feet per second unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> fps(Metric) # m⋅s⁻¹
0.3048

julia> fps(KKH) # km⋅h⁻¹
1.0972799999999998

julia> fps(MPH) # mi⋅h⁻¹
0.6818181818181819
```
