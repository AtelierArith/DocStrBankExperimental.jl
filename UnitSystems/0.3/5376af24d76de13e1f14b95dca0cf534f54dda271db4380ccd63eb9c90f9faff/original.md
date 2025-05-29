```Julia
meancalorie(U::UnitSystem) = energy(𝟐^2*𝟓*𝟑^2/𝟒𝟑,U,InternationalMean)
```

Heat energy required to raise 1 g of water by 1 Kelvin (`cal`) in `InternationalMean` units.

```Julia
julia> meancalorie(InternationalMean) # J
4.186046511627907

julia> meancalorie(Metric) # J
4.186841954605035

julia> meancalorie(English) # ft⋅lb
3.088056150722716
```
