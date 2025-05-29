```
crosspath(len::Integer, g::Graph)
```

`g`を`len`回複製し、各頂点をそのコピーとパスで接続するグラフを返します。

### 実装ノート

入力グラフのeltypeを保持します。生成されたグラフの頂点数がeltypeを超えるとエラーになります。

# 例

```jldoctest
julia> using Graphs

julia> g = crosspath(3, path_graph(3))
{9, 12} undirected simple Int64 graph

julia> collect(edges(g))
12-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 4
 Edge 2 => 3
 Edge 2 => 5
 Edge 3 => 6
 Edge 4 => 5
 Edge 4 => 7
 Edge 5 => 6
 Edge 5 => 8
 Edge 6 => 9
 Edge 7 => 8
 Edge 8 => 9
```
