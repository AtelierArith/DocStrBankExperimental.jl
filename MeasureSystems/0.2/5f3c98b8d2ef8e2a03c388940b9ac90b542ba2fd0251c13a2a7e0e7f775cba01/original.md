```Julia
luminousintensity : [JA⁻²], [J], [J], [J], [J]
luminousintensity(U::UnitSystem,S::UnitSystem) = luminousflux(U,S)/solidangle(U,S)
luminousintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousintensity(U,S)
JA⁻² [ħ⁻¹𝘤⁴mₑ²Kcd⋅ϕ⁻³g₀⁻²] Unified
```

Perceived power of light or `luminousintensity` (cd, lm⋅rad⁻²), unit conversion factor.
