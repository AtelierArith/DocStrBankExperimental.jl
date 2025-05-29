```Julia
luminousintensity(U::UnitSystem,S::UnitSystem) = luminousflux(U,S)/solidangle(U,S)
luminousintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousintensity(U,S)
```

Perceived power of light or `luminousintensity` (cd, lm⋅rad⁻²), unit conversion factor.
