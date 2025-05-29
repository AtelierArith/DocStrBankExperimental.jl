```Julia
luminousflux(U::UnitSystem,S::UnitSystem) = luminousenergy(U,S)*frequency(U,S)
luminousflux(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousflux(U,S)
```

Perceived power of light or `luminousflux` (lm, cd⋅rad⋅²), unit conversion factor.
