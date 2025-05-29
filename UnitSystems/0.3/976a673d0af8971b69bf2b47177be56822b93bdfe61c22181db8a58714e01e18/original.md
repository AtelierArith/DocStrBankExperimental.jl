```Julia
mps(U::UnitSystem) = mile(U)/second(U)
```

Miles per second unit of `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> mps(KKH) # km⋅h⁻¹
5793.6384

julia> mps(MPH) # mi⋅h⁻¹
3600.0

julia> mps(Nautical) # nm⋅h⁻¹
3124.04095504942
```
