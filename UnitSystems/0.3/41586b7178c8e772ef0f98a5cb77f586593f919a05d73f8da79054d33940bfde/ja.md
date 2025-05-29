```Julia
kilocalorie(U::UnitSystem) = energy(𝟐^5*𝟓^4*𝟑^2/𝟒𝟑,U,International)
```

1 kgの水を1ケルビン（`kcal`）上昇させるために必要な熱エネルギーを`International`単位で表します。

```Julia
julia> kilocalorie(International) # J
4186.046511627907

julia> kilocalorie(Metric) # J
4186.737323211057

julia> kilocalorie(English) # ft⋅lb
3087.9789785668913
```
