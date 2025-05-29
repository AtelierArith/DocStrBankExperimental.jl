```Julia
earthmeter(U::UnitSystem) = greatcircle(U)/𝟐^9/𝟓^7
```

Meridian unit of `length` as originally defined in France (m or ft).

```Julia
julia> earthmeter(CGS) # cm
100.14480543039193

julia> earthmeter(English) # ft
3.2855907293435678

julia> earthmeter(Meridian) # em
1
```
