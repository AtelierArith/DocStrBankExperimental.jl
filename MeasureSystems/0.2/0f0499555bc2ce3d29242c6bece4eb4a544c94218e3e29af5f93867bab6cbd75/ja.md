```Julia
angularlength : [LA⁻¹], [L], [L], [L], [L]
angularlength(U::UnitSystem,S::UnitSystem) = length(U,S)/angle(U,S)
angularlength(v::Real,U::UnitSystem,S::UnitSystem) = v/angularlength(U,S)
LA⁻¹ [ħ⋅𝘤⁻¹mₑ⁻¹g₀] 統一

```

単位の `length` あたりの `angle` (m⋅rad⁻¹)、単位変換係数。

```Julia
julia> angularlength(CGS,Metric) # cm⋅m⁻¹
2⁻²5⁻² = 0.010000000000000002 [m]/[cm] ガウス -> メトリック

julia> angularlength(English,Metric) # ft⋅m⁻¹
ft = 0.3048 [m]/[ft] 英語 -> メトリック
```
