```
SimpleGraph{T}(nv, ne; rng=nothing, seed=nothing)
```

`nv` 頂点と `ne` 辺を持つランダムな `SimpleGraph{T}` を構築します。このグラフは、すべてのそのようなグラフから均等にサンプリングされます。`seed >= 0` の場合、ランダムジェネレーターはこの値でシードされます。指定されていない場合、要素型 `T` は `nv` の型になります。

### 参照

[`erdos_renyi`](@ref)

## 例

```jldoctest
julia> using Graphs

julia> SimpleGraph(5, 7)
{5, 7} 無向単純 Int64 グラフ
```
