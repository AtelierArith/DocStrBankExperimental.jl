```Julia
mps(U::UnitSystem) = mile(U)/second(U)
```

秒速の単位 `speed` (m⋅s⁻¹ または ft⋅s⁻¹)。

```Julia
julia> mps(KKH) # km⋅h⁻¹
5793.6384

julia> mps(MPH) # mi⋅h⁻¹
3600.0

julia> mps(Nautical) # nm⋅h⁻¹
3124.04095504942
```
