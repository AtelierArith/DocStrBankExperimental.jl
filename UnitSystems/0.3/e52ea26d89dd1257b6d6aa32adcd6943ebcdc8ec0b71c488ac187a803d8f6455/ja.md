```Julia
knot(U::UnitSystem) = nauticalmile(U)/hour(U)
```

ノットは`speed`の単位（m⋅s⁻¹またはft⋅s⁻¹）です。

```Julia
julia> knot(Metric) # m⋅s⁻¹
0.515148176082263

julia> knot(KKH) # km⋅h⁻¹
1.8545334338961466

julia> knot(MPH) # mi⋅h⁻¹
1.1523536508640457
```
