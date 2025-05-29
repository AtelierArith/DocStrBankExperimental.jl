```Julia
luminousflux : [J], [J], [J], [J], [J]
luminousflux(U::UnitSystem,S::UnitSystem) = luminousenergy(U,S)*frequency(U,S)
luminousflux(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousflux(U,S)
J [ħ⁻¹𝘤⁴mₑ²Kcd⋅ϕ⁻¹g₀⁻²] Unified
```

光の知覚された力または `luminousflux` (lm, cd⋅rad⋅²)、単位変換係数。
