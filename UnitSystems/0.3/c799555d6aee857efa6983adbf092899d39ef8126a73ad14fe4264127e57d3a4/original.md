```Julia
calorie(U::UnitSystem) = kilocalorie(U)/𝟐^3/𝟓^3
```

Heat energy required to raise 1 g of water by 1 Kelvin (`cal`) in `International` units.

```Julia
julia> calorie(International) # J
4.186046511627907

julia> calorie(Metric) # J
4.186737323211057

julia> calorie(English) # ft⋅lb
3.087978978566891
```
