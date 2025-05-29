```Julia
impulse(U::UnitSystem,S::UnitSystem) = force(U,S)*time(U,S)
impulse(v::Real,U::UnitSystem,S::UnitSystem) = v/impulse(U,S)
```

線形 `impulse` または `force` に `time` を掛けたもの (N⋅s, kg⋅m⋅s⁻¹)、単位変換係数。

```Julia
julia> impulse(CGS,Metric) # N⋅dyn⁻¹
1.0e-5

julia> impulse(CGS,English) # lb⋅dyn⁻¹
2.248089430997105e-6

julia> impulse(English,Metric) # N⋅lb⁻¹
4.4482216152605
```
