```Julia
mph(U::UnitSystem) = mile(U)/hour(U)
```

Miles per hour unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> mph(Metric) # m⋅s⁻¹
0.4470400000000001

julia> mph(KKH) # km⋅h⁻¹
1.6093439999999999

julia> mph(Nautical) # nm⋅h⁻¹
0.8677891541803945
```
