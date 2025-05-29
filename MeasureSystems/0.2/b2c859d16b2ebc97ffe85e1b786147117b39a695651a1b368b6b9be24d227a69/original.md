```Julia
luminousenergy : [TJ], [TJ], [TJ], [TJ], [TJ]
luminousenergy(U::UnitSystem,S::UnitSystem) = luminousflux(U,S)*time(U,S)
luminousenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousenergy(U,S)
TJ [𝘤²mₑ⋅Kcd⋅g₀⁻¹] Unified
```

Perceived quantity of light or `luminousenergy` (lm⋅s, cd⋅s⋅sr), unit conversion factor.

```Julia
julia> luminousenergy(IAU,Metric) # s⋅day⁻¹
2⁷3³5² = 86400.0 [s]/[D] IAU☉ -> Metric
```
