```Julia
radian(U::UnitSystem) = angle(𝟏,U,Metric)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A [ϕ] 統一

```

`angle`の単位は無次元（rad）です。

```Julia
julia> radian(Engineering) # rad
𝟏 = 1.0 [rad] 工学

julia> radian(MetricDegree) # deg
τ⁻¹2³3²5 = 57.29577951308232 [deg] メトリック度

julia> radian(MetricArcminute) # amin
τ⁻¹2⁵3³5² = 3437.7467707849396 [amin] メトリック分

julia> radian(MetricArcsecond) # asec
τ⁻¹2⁷3⁴5³ = 206264.80624709636 [asec] メトリック秒

julia> radian(MetricGradian) # gon
τ⁻¹2⁴5² = 63.66197723675814 [gon] メトリックグラジアン
```
