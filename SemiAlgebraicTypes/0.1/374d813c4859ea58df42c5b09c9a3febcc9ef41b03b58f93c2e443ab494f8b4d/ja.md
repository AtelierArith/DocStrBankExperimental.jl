```
Mesh{T}
```

点の配列（`Vector{T}`）、エッジの配列（`Vector{Int64}`）、および面の配列（`Vector{Int64}`）に対応するメッシュ。

## 例

```jldoctest
julia> mesh(Float64);

julia> mesh([[cos(i*pi/5), sin(i*pi/5), 0.0] for i in 1:10], Edge[], [[1,i,i+1] for i in 1:9]);
```

**フィールド:**

  * `points  ::Matrix{T}`: 点の配列
  * `edges   ::Vector{Vector{Int64}}`: エッジの配列
  * `faces   ::Vector{Vector{Int64}}`: 面の配列
  * `normals ::Matrix{T}`: 法線の配列
  * `attr    ::Dict{Symbol,Any}`: 属性
