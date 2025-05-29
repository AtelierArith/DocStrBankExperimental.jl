```Julia
bradian(U::UnitSystem) = angle(τ/𝟐^8,U,Metric)
```

`angle`の単位で、`turn`を`𝟐^8`または`256`の部分に分割します（ラジアン）。

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
