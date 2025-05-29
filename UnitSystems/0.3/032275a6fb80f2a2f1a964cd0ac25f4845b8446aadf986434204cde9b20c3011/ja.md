```Julia
ms(U::UnitSystem) = meter(U)/second(U)
```

メートル毎秒の単位 `speed` (m⋅s⁻¹ または ft⋅s⁻¹)。

```Julia
julia> ms(KKH) # km⋅h⁻¹
3.599999999999999

julia> ms(MPH) # mi⋅h⁻¹
2.236936292054402

julia> ms(Nautical) # nm⋅h⁻¹
1.9411890528373181
```
