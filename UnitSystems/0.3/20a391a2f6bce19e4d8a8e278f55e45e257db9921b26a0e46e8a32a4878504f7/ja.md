```Julia
gravity(U::UnitSystem) = # 質量*加速度/力
```

技術工学単位で使用される重力の参照 (kg⋅m⋅N⁻¹⋅s⁻²)。

```Julia
julia> gravity(Metric)
1

julia> gravity(Engineering) # m⋅kg⋅N⁻¹⋅s⁻²
9.80665

julia> gravity(English) # ft⋅lbm⋅lbf⁻¹⋅s⁻²
32.17404855643044
```
