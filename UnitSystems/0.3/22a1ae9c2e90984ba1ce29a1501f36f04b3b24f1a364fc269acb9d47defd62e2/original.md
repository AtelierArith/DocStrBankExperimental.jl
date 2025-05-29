```Julia
tontnt(U::UnitSystem) = giga*calorie(U)
```

Ton TNT equivalent reference unit of `energy` (J or lb⋅ft).

```Julia
julia> tontnt(Metric) # J
4.186737323211057e9

julia> tontnt(CGS) # erg
4.186737323211056e16

julia> tontnt(British) # lb⋅ft
3.0879789785668917e9
```
