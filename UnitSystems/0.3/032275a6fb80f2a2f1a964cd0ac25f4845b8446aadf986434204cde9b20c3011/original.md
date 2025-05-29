```Julia
ms(U::UnitSystem) = meter(U)/second(U)
```

Meters per second unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> ms(KKH) # km⋅h⁻¹
3.599999999999999

julia> ms(MPH) # mi⋅h⁻¹
2.236936292054402

julia> ms(Nautical) # nm⋅h⁻¹
1.9411890528373181
```
