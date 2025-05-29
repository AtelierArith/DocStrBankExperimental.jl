```
SimpleDiGraph{T}(nv, ne; seed=-1)
```

`nv` 頂点と `ne` 辺を持つランダムな `SimpleDiGraph{T}` を構築します。グラフはすべてのそのようなグラフから均等にサンプリングされます。`seed >= 0` の場合、ランダムジェネレーターはこの値でシードされます。指定されていない場合、要素型 `T` は `nv` の型です。

### 参照

[`erdos_renyi`](@ref)

## 例

```jldoctest
julia> SimpleDiGraph(5, 7)
{5, 7} directed simple Int64 graph
```
