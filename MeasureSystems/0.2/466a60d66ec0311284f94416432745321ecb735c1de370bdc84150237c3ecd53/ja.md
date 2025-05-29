```Julia
gradian(U::UnitSystem) = angle(𝟏,U,MetricGradian)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A⋅(τ⋅2⁻⁴5⁻² = 0.015707963267948967) [ϕ] 統一

Unit of `angle` which divides a `turn` into `400` parts (rad).

```

Julia julia> gradian(Engineering) # rad τ⋅2⁻⁴5⁻² = 0.015707963267948967 [rad] 工学

julia> gradian(MetricDegree) # deg 2⁻¹3²5⁻¹ = 0.9 [deg] メトリック度

julia> gradian(MetricArcminute) # amin 2⋅3³ = 54.0 [amin] メトリック分

julia> gradian(MetricArcsecond) # asec 2³3⁴5 = 3240.0 [asec] メトリック秒

julia> gradian(MetricGradian) # gon 𝟏 = 1.0 [gon] メトリックグラジアン ```
