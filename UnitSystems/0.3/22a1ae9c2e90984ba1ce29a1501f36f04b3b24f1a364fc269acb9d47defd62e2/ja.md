```Julia
tontnt(U::UnitSystem) = giga*calorie(U)
```

トン TNT 相当の基準単位 `energy` (J または lb⋅ft)。

```Julia
julia> tontnt(Metric) # J
4.186737323211057e9

julia> tontnt(CGS) # erg
4.186737323211056e16

julia> tontnt(British) # lb⋅ft
3.0879789785668917e9
```
