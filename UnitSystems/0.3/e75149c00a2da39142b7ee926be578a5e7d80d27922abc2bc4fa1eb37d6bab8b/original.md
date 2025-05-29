```Julia
fpm(U::UnitSystem) = feet(U)/minute(U)
```

Feet per minute unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> fpm(CGS) # cm⋅s⁻¹
0.508

julia> fpm(IPS) # in⋅s⁻¹
0.19999999999999993

julia> fpm(English) # ft⋅s⁻¹
0.016666666666666666
```
