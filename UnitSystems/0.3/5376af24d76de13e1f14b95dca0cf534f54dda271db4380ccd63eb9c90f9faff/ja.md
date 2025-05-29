```Julia
meancalorie(U::UnitSystem) = energy(𝟐^2*𝟓*𝟑^2/𝟒𝟑,U,InternationalMean)
```

1 gの水を1ケルビン上昇させるのに必要な熱エネルギー（`cal`）を`InternationalMean`単位で。

```Julia
julia> meancalorie(InternationalMean) # J
4.186046511627907

julia> meancalorie(Metric) # J
4.186841954605035

julia> meancalorie(English) # ft⋅lb
3.088056150722716
```
