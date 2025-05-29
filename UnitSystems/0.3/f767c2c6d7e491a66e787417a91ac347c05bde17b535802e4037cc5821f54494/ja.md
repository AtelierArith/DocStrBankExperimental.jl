```Julia
admiraltymile(U::UnitSystem) = length(𝟐^6*𝟓*𝟏𝟗,U,English)
```

クラークの等距離半径によって定義された歴史的海里 (m または ft)。

```Julia
julia> admiraltymile(Metric) # m
1853.1840000000002

julia> admiraltymile(English) # ft
6080

julia> admiraltymile(Nautical) # nm
0.9992723593592421
```
