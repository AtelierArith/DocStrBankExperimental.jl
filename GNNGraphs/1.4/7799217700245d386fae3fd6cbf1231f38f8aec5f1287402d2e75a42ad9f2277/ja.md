```
has_edge(g::GNNHeteroGraph, edge_t, i, j)
```

`g`内のノード`i`からノード`j`へのエッジのタイプ`edge_t`が存在する場合は`true`を返します。

# 例

```jldoctest
julia> g = rand_bipartite_heterograph((2, 2), (4, 0), bidirected=false)
GNNHeteroGraph:
  num_nodes: Dict(:A => 2, :B => 2)
  num_edges: Dict((:A, :to, :B) => 4, (:B, :to, :A) => 0)

julia> has_edge(g, (:A,:to,:B), 1, 1)
true

julia> has_edge(g, (:B,:to,:A), 1, 1)
false
```
