```Julia
greatcircle(U::UnitSystem) = τ*earthradius(U)
```

標準的な地球の二体円の`length`を単位（mまたはft）に一致させて近似します。

```Julia
julia> greatcircle(KKH) # km
40057.92217215678

julia> greatcircle(Nautical) # nm
21600.0

julia> greatcircle(IAU) # au
0.0002677706706968308
```
