```
struct EquispacedGrid{T} <: AbstractEquispacedGrid{T}
```

区間 [a,b] に n 点を持つ等間隔グリッド。端点を含みます。ステップは (b-a)/(n-1) です。

# 例

```jldocs
julia> EquispacedGrid(4,0,1)
4-element EquispacedGrid{Float64}:
 0.0
 0.3333333333333333
 0.6666666666666666
 1.0
```
