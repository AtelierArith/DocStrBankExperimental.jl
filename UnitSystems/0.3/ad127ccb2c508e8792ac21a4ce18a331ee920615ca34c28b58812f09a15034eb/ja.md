```Julia
rpm(U::UnitSystem) = turn(U)/minute(U)
```

毎分の回転数 `rpm` 単位の `angularfrequency` (rad⋅s⁻¹)。

```Julia
julia> rpm(Engineering) # rad⋅s⁻¹
0.10471975511965977

julia> rpm(MetricGradian) # gon⋅s⁻¹
6.666666666666667

julia> rpm(MetricDegree) # deg⋅s⁻¹
6.0

julia> rpm(MetricArcminute) # amin⋅s⁻¹
360.0

julia> rpm(MetricArcsecond) # asec⋅s⁻¹
21600.0

julia> rpm(MPH) # rad⋅h⁻¹
376.99111843077526

julia> rpm(IAU) # rad⋅D⁻¹
9047.786842338604
```
