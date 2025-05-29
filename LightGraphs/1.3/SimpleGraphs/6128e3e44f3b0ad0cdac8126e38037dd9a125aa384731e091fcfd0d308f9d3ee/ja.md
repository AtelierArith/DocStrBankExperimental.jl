```
SimpleGraph{T}(nv, ne; seed=-1)
```

`nv` 頂点と `ne` 辺を持つランダムな `SimpleGraph{T}` を構築します。グラフはすべてのそのようなグラフから均等にサンプリングされます。`seed >= 0` の場合、ランダム生成器はこの値でシードされます。指定されていない場合、要素型 `T` は `nv` の型です。

### 参照

[`erdos_renyi`](@ref)

## 例

```jldoctest
julia> SimpleGraph(5, 7)
{5, 7} 無向単純 Int64 グラフ
```
