```
struct PeriodicEquispacedGrid{T} <: AbstractEquispacedGrid{T}
```

周期的等間隔グリッドは、右端点を省略した等間隔グリッドです。ステップサイズは (b-a)/n です。

# 例

```jldocs
julia> PeriodicEquispacedGrid(4,0,1)
4-element PeriodicEquispacedGrid{Float64}:
 0.0
 0.25
 0.5
 0.75
```
