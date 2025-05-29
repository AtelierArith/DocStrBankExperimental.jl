```Julia
calorie(U::UnitSystem) = kilocalorie(U)/𝟐^3/𝟓^3
```

1 gの水を1ケルビン上昇させるのに必要な熱エネルギー（`cal`）を`International`単位で表します。

```Julia
julia> calorie(International) # J
4.186046511627907

julia> calorie(Metric) # J
4.186737323211057

julia> calorie(English) # ft⋅lb
3.087978978566891
```
