```Julia
fpm(U::UnitSystem) = feet(U)/minute(U)
```

フィート毎分の単位 `speed` (m⋅s⁻¹ または ft⋅s⁻¹)。

```Julia
julia> fpm(CGS) # cm⋅s⁻¹
0.508

julia> fpm(IPS) # in⋅s⁻¹
0.19999999999999993

julia> fpm(English) # ft⋅s⁻¹
0.016666666666666666
```
