```Julia
squaredegree(U::UnitSystem) = solidangle(𝟏,U,MetricDegree)
solidangle : [A²], [𝟙], [𝟙], [𝟙], [𝟙]
A²⋅(τ²2⁻⁶3⁻⁴5⁻² = 0.0003046174197867087) [ϕ²] Unified
```

`solidangle`の単位は`degree`の二乗（rad²）です。

```Julia
julia> squaredegree(Engineering) # rad²
τ²2⁻⁶3⁻⁴5⁻² = 0.0003046174197867087 [rad²] Engineering

julia> squaredegree(MetricDegree) # deg²
𝟏 = 1.0 [deg²] MetricDegree

julia> squaredegree(MetricArcminute) # amin²
2⁴3²5² = 3600.0 [amin²] MetricArcminute

julia> squaredegree(MetricArcsecond) # asec²
2⁸3⁴5⁴ = 1.296×10⁷ [asec²] MetricArcsecond

julia> squaredegree(MetricGradian) # gon²
2²3⁻⁴5² = 1.2345679012345678 [gon²] MetricGradian
```
