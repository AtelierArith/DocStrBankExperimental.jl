```
SimpleGraph(::Type{T})
```

0頂点と0辺を持つ空の`SimpleGraph{T}`を構築します。

## 例

```jldoctest
julia> using Graphs

julia> SimpleGraph(UInt8)
{0, 0} 無向単純UInt8グラフ
```
