```Julia
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
angle(U::UnitSystem,S::UnitSystem) = angle(U,S)
angle(v::Real,U::UnitSystem,S::UnitSystem) = v/angle(U,S)
A [ϕ] 統一

一次元角度または `angle` (rad) の範囲、単位変換係数。

```

Julia julia> angle(CGS,Metric) # rad⋅rad⁻¹ 𝟏 = 1.0 [𝟙]/[𝟙] Metric -> Gauss ```
