```Julia
degree(U::UnitSystem) = angle(𝟏,U,MetricDegree)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A⋅(τ⋅2⁻³3⁻²5⁻¹ = 0.017453292519943295) [ϕ] 統一

Unit of `angle` which divides a `turn` into `360` parts (rad).

```

Julia julia> degree(Engineering) # rad τ⋅2⁻³3⁻²5⁻¹ = 0.017453292519943295 [rad] 工学

julia> degree(MetricDegree) # deg 𝟏 = 1.0 [deg] メトリック度

julia> degree(MetricArcminute) # amin 2²3⋅5 = 60.0 [amin] メトリック分

julia> degree(MetricArcsecond) # asec 2⁴3²5² = 3600.0 [asec] メトリック秒

julia> degree(MetricGradian) # gon 2⋅3⁻²5 = 1.1111111111111112 [gon] メトリックグラジアン ```
