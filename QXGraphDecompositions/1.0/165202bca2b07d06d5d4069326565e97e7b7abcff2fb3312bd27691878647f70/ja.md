ラベル付きグラフを表す構造体。頂点が提供されていない場合は、各頂点のためにユニークなシンボルが作成され、グラフのライフタイム中は変更されません。

# 例

```julia-repl
julia> g = LabeledGraph()
LabeledGraph({0, 0} undirected simple Int64 graph, Symbol[])

julia> add_vertex!(g, :a_vertex_label)
1-element Array{Symbol,1}:
 :a_vertex_label

julia> g.labels[1]
:a_vertex_label
```
