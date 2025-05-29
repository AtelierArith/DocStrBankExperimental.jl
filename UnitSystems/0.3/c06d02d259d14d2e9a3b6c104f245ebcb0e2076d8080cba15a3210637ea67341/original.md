```Julia
bradian(U::UnitSystem) = angle(τ/𝟐^8,U,Metric)
```

Unit of `angle` which divides a `turn` into `𝟐^8` or `256` parts (rad).

```Julia
julia> bradian(Engineering) # rad
0.02454369260617026

julia> bradian(MetricDegree) # deg
80.57218994027201

julia> bradian(MetricArcminute) # amin
290059.8837849793

julia> bradian(MetricArcsecond) # asec
1.0442155816259253e9

julia> bradian(MetricGradian) # gon
99.47183943243458
```
