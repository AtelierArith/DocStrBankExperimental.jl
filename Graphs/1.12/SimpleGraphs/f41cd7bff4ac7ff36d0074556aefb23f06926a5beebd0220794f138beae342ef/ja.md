```
SimpleGraph{T}(n=0)
```

`n` 頂点と 0 辺を持つ `SimpleGraph{T}` を構築します。指定されていない場合、要素型 `T` は `n` の型です。

## 例

```jldoctest
julia> using Graphs

julia> SimpleGraph(UInt8(10))
{10, 0} 無向単純 UInt8 グラフ
```
