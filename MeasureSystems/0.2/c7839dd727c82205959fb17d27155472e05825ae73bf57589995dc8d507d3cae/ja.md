```Julia
bradian(U::UnitSystem) = angle(τ/𝟐^8,U,Metric)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A⋅(τ⋅2⁻⁸ = 0.02454369260617026) [ϕ] 統一

Unit of `angle` which divides a `turn` into `𝟐^8` or `256` parts (rad).

```

Julia julia> bradian(Engineering) # rad τ⋅2⁻⁸ = 0.02454369260617026 [rad] 工学

julia> bradian(MetricDegree) # deg 2⁻⁵3²5 = 1.40625 [deg] メトリック度

julia> bradian(MetricArcminute) # amin 2⁻³3³5² = 84.375 [amin] メトリック分

julia> bradian(MetricArcsecond) # asec 2⁻¹3⁴5³ = 5062.5 [asec] メトリック秒

julia> bradian(MetricGradian) # gon 2⁻⁴5² = 1.5625 [gon] メトリックグラジアン ```
