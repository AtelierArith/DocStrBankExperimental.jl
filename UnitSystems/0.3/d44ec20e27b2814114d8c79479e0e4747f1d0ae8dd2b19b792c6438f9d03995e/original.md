```Julia
ounce(U::UnitSystem) = pound(U)/𝟐^4
```

English `ounce` unit of `mass` (kg or lb).

```Julia
julia> ounce(Metric) # kg
0.028349523125

julia> ounce(CGS) # g
28.349523125000005

julia> ounce(English) # lb
0.0625

julia> ounce(British) # slug
0.0019425593857229535

julia> ounce(Gravitational) # hyl
0.0028908468360755207
```
