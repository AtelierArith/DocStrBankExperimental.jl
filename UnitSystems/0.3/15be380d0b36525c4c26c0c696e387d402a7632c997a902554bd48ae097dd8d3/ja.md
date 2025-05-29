```Julia
angle(U::UnitSystem,S::UnitSystem) = angle(U,S)
angle(v::Real,U::UnitSystem,S::UnitSystem) = v/angle(U,S)
```

一次元の角度または `angle` (rad)、単位変換係数。

```Julia
julia> angle(CGS,Metric) # rad⋅rad⁻¹
1
```
