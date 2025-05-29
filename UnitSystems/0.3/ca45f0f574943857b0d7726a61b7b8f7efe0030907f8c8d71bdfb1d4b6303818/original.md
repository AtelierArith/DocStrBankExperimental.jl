```Julia
greatcircle(U::UnitSystem) = τ*earthradius(U)
```

Approximate `length` of standard Earth two-body circle consistent with units (m or ft).

```Julia
julia> greatcircle(KKH) # km
40057.92217215678

julia> greatcircle(Nautical) # nm
21600.0

julia> greatcircle(IAU) # au
0.0002677706706968308
```
