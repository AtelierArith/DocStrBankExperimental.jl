```Julia
luminousenergy(U::UnitSystem,S::UnitSystem) = luminousflux(U,S)*time(U,S)
luminousenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousenergy(U,S)
```

Perceived quantity of light or `luminousenergy` (lm⋅s, cd⋅s⋅sr), unit conversion factor.

```Julia
julia> luminousenergy(IAU,Metric) # s⋅day⁻¹
86399.99999999997
```
