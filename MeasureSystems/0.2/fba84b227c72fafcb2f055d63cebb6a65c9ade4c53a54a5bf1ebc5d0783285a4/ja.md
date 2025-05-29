```Julia
fps(U::UnitSystem) = feet(U)/second(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹⋅(𝘤⁻¹ft = 1.0167033621639674×10⁻⁹) [𝘤] 統一

`speed`のフィート毎秒単位 (m⋅s⁻¹ または ft⋅s⁻¹)。

```

Julia julia> fps(Metric) # m⋅s⁻¹ ft = 0.3048 [m⋅s⁻¹] メトリック

julia> fps(KKH) # km⋅h⁻¹ ft⋅2⋅3²5⁻¹ = 1.09728 [km⋅h⁻¹] KKH

julia> fps(MPH) # mi⋅h⁻¹ 2⁻¹3⋅5⋅11⁻¹ = 0.6818181818181819 [mi⋅h⁻¹] MPH ```
