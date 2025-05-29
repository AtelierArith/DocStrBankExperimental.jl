```Julia
jansky(U::UnitSystem) = fluence(𝟏𝟎^-26,U,Metric)
```

スペクトル放射照度の基準単位 (kg⋅s⁻² または lb⋅ft⁻¹)。

```Julia
julia> jansky(Metric) # kg⋅s⁻²
1.0000000000000015e-26

julia> jansky(CGS) # g⋅s⁻²
1.0000000000000019e-23

julia> jansky(English) # lb⋅ft⁻¹
6.852176585679186e-28
```
