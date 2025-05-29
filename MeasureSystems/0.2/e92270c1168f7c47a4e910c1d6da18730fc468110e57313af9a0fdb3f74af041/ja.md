```Julia
turn(U::UnitSystem) = 2π/angle(U)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A⋅(τ = 6.283185307179586) [ϕ] 統一

完全な円からの回転 `angle` の完全な回転。

```

Julia julia> turn(Engineering) # rad τ = 6.283185307179586 [rad] 工学

julia> turn(MetricDegree) # deg 2³3²5 = 360.0 [deg] メトリック度

julia> turn(MetricArcminute) # amin 2⁵3³5² = 21600.0 [amin] メトリック分

julia> turn(MetricArcsecond) # asec 2⁷3⁴5³ = 1.296×10⁶ [asec] メトリック秒

julia> turn(MetricGradian) # gon 2⁴5² = 400.0 [gon] メトリックグラジアン ```
