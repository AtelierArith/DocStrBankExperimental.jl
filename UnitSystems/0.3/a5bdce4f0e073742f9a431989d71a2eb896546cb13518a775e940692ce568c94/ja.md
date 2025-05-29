```Julia
luminousenergy(U::UnitSystem,S::UnitSystem) = luminousflux(U,S)*time(U,S)
luminousenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousenergy(U,S)
```

光の知覚量または `luminousenergy` (lm⋅s, cd⋅s⋅sr)、単位変換係数。

```Julia
julia> luminousenergy(IAU,Metric) # s⋅day⁻¹
86399.99999999997
```
