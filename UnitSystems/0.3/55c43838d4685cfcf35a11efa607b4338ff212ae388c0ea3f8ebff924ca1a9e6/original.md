```Julia
lightyear(U::UnitSystem) = year(U)*lightspeed(U)
```

Unit of `length` defined by distance traveled by light in 1 `year` unit.

```Julia
julia> lightyear(Metric) # m
9.4607304725808e15

julia> lightyear(English) # ft
3.103914197040945e16

julia> lightyear(IAU) # au
63241.07708426628
```
