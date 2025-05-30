```
SimpleGraph{T}(g::SimpleGraph)
```

gのコピーを作成します。要素型`T`が指定されている場合、gの頂点はこの型に変換されます。そうでない場合、要素型はgと同じです。

## 例

```jldoctest
julia> using Graphs

julia> g = complete_graph(5)
{5, 10} 無向単純 Int64 グラフ

julia> SimpleGraph{UInt8}(g)
{5, 10} 無向単純 UInt8 グラフ
```
