```Julia
earthmeter(U::UnitSystem) = greatcircle(U)/𝟐^9/𝟓^7
```

フランスで元々定義された`length`の子午線単位（mまたはft）。

```Julia
julia> earthmeter(CGS) # cm
100.14480543039193

julia> earthmeter(English) # ft
3.2855907293435678

julia> earthmeter(Meridian) # em
1
```
