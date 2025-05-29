```Julia
solidangle(U::UnitSystem,S::UnitSystem) = angle(U,S)^2
solidangle(v::Real,U::UnitSystem,S::UnitSystem) = v/solidangle(U,S)
```

二次元角度または `solidangle` (rad²) の範囲、単位変換係数。

```Julia
julia> solidangle(CGS,Metric) # rad²⋅rad⁻²
1
```
