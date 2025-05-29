```Julia
luminousflux : [J], [J], [J], [J], [J]
luminousflux(U::UnitSystem,S::UnitSystem) = luminousenergy(U,S)*frequency(U,S)
luminousflux(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousflux(U,S)
J [ħ⁻¹𝘤⁴mₑ²Kcd⋅ϕ⁻¹g₀⁻²] Unified
```

Perceived power of light or `luminousflux` (lm, cd⋅rad⋅²), unit conversion factor.
