```Julia
knot(U::UnitSystem) = nauticalmile(U)/hour(U)
```

Nautical miles per hour unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> knot(Metric) # m⋅s⁻¹
0.515148176082263

julia> knot(KKH) # km⋅h⁻¹
1.8545334338961466

julia> knot(MPH) # mi⋅h⁻¹
1.1523536508640457
```
