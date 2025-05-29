```
struct MidpointEquispacedGrid{T} <: AbstractEquispacedGrid{T}
```

MidpointEquispacedグリッドは、等間隔のサブ区間の中心にグリッドポイントがある等間隔グリッドです。言い換えれば、これはDCT-IIグリッドです。ステップは`(b-a)/n`です。

# 例

```jldocs
julia> MidpointEquispacedGrid(4,0,1)
4-element MidpointEquispacedGrid{Float64}:
 0.125
 0.375
 0.6249999999999999
 0.875
```
