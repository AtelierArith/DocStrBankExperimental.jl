```Julia
arcsecond(U::UnitSystem) = angle(𝟏,U,MetricArcsecond)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A⋅(τ⋅2⁻⁷3⁻⁴5⁻³ = 4.84813681109536×10⁻⁶) [ϕ] Unified
```

Unit of `angle` which divides a `arcminute` into `60` parts (rad).

```Julia
julia> arcsecond(Engineering) # rad
τ⋅2⁻⁷3⁻⁴5⁻³ = 4.84813681109536×10⁻⁶ [rad] Engineering

julia> arcsecond(MetricDegree) # deg
2⁻⁴3⁻²5⁻² = 0.00027777777777777783 [deg] MetricDegree

julia> arcsecond(MetricArcminute) # amin
2⁻²3⁻¹5⁻¹ = 0.016666666666666666 [amin] MetricArcminute

julia> arcsecond(MetricArcsecond) # asec
𝟏 = 1.0 [asec] MetricArcsecond

julia> arcsecond(MetricGradian) # gon
2⁻³3⁻⁴5⁻¹ = 0.00030864197530864197 [gon] MetricGradian
```
