```
SimpleGraph(edge_list::Vector)
```

ベクトルのエッジから `SimpleGraph` を構築します。要素の型は `edge_list` のエッジから取得されます。頂点の数は `edge_list` のエッジで使用される最大の値です。

### 実装ノート

このコンストラクタは、`edge_list` が辞書順にソートされていて、重複が含まれていない場合に最も速く動作します。

### 参照

[`SimpleGraphFromIterator`](@ref)

## 例

```jldoctest
julia> using Graphs

julia> el = Edge.([ (1, 2), (1, 5) ])
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 5

julia> SimpleGraph(el)
{5, 2} undirected simple Int64 graph
```
