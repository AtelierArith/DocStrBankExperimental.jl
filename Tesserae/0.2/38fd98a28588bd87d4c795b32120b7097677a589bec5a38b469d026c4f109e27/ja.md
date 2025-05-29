```
neighboringnodes(x::Vec, r::Real, mesh::CartesianMesh)
```

`x`の周りの隣接ノードの`CartesianIndices`を返します。`r`は探索エリアの範囲を示します。1Dの場合、範囲`a`は`x-r*h ≤ a < x+r*h`となり、ここで`h`は`spacing(mesh)`です。

# 例

```jldoctest
julia> mesh = CartesianMesh(1, (0,5))
6-element CartesianMesh{1, Float64, Vector{Float64}}:
 [0.0]
 [1.0]
 [2.0]
 [3.0]
 [4.0]
 [5.0]

julia> neighboringnodes(Vec(1.5), 1, mesh)
CartesianIndices((2:3,))

julia> neighboringnodes(Vec(1.5), 3, mesh)
CartesianIndices((1:5,))
```
