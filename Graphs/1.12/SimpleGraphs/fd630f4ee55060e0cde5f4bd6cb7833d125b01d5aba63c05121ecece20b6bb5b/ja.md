```
SimpleDiGraph{T}(g::SimpleDiGraph)
```

gのコピーを作成します。要素型`T`が指定されている場合、gの頂点はこの型に変換されます。そうでない場合、要素型はgと同じです。

## 例

```jldoctest
julia> using Graphs

julia> g = complete_digraph(5)
{5, 20} directed simple Int64 graph

julia> SimpleDiGraph{UInt8}(g)
{5, 20} directed simple UInt8 graph
```
