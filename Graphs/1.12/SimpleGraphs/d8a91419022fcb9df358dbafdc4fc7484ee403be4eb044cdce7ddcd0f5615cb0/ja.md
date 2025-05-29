```
SimpleDiGraph(edge_list::Vector)
```

ベクトルのエッジから `SimpleDiGraph` を構築します。要素の型は `edge_list` のエッジから取得されます。頂点の数は `edge_list` のエッジで使用される最大の値です。

### 実装ノート

このコンストラクタは、`edge_list` が辞書式順序でソートされており、重複が含まれていない場合に最も高速に動作します。

### 参照

[`SimpleDiGraphFromIterator`](@ref)

## 例

```jldoctest
julia> using Graphs

julia> el = Edge.([ (1, 3), (1, 5), (3, 1) ])
3-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 3
 Edge 1 => 5
 Edge 3 => 1
 
julia> SimpleDiGraph(el)
{5, 3} directed simple Int64 graph
```
