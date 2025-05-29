```Julia
lightyear(U::UnitSystem) = year(U)*lightspeed(U)
```

1 `year` 単位で光が移動する距離によって定義される `length` の単位。

```Julia
julia> lightyear(Metric) # m
9.4607304725808e15

julia> lightyear(English) # ft
3.103914197040945e16

julia> lightyear(IAU) # au
63241.07708426628
```
