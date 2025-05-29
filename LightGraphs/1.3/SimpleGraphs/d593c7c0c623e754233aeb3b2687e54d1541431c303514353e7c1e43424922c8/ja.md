```
SimpleDiGraph{T}(n=0)
```

`n` 頂点と 0 辺を持つ `SimpleDiGraph{T}` を構築します。指定されていない場合、要素型 `T` は `n` の型です。

## 例

```jldoctest
julia> SimpleDiGraph(UInt8(10))
{10, 0} directed simple UInt8 graph
```
