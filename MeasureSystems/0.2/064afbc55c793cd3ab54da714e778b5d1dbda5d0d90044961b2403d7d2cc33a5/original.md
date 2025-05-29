```Julia
steradian(U::UnitSystem) = solidangle(𝟏,U,Metric)
solidangle : [A²], [𝟙], [𝟙], [𝟙], [𝟙]
A² [ϕ²] Unified
```

Unit of `solidangle` which is dimensionless (rad²).

```Julia
julia> steradian(Engineering) # rad²
𝟏 = 1.0 [rad²] Engineering

julia> steradian(MetricDegree) # deg²
τ⁻²2⁶3⁴5² = 3282.8063500117446 [deg²] MetricDegree

julia> steradian(MetricArcminute) # amin²
τ⁻²2¹⁰3⁶5⁴ = 1.181810286004228×10⁷ [amin²] MetricArcminute

julia> steradian(MetricArcsecond) # asec²
τ⁻²2¹⁴3⁸5⁶ = 4.254517029615221×10¹⁰ [asec²] MetricArcsecond

julia> steradian(MetricGradian) # gon²
τ⁻²2⁸5⁴ = 4052.8473456935117 [gon²] MetricGradian
```
