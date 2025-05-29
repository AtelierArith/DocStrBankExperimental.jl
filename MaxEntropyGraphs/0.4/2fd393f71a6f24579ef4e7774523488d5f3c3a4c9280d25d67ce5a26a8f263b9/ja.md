```
V_motifs(G::Graphs.SimpleGraph, i::Int, j::Int; membership::Vector=Graphs.bipartite_map(G))
```

グラフ `G` におけるノード `i` と `j` の間の V-モチーフの出現回数をカウントします。

*注意*：

1. グラフの二部性は明示的にチェックされません。
2. これはグラフ内の実際のノード番号を使用し、特定の層での番号付けではありません。

# 引数

  * `membership`: グラフの二部マッピング。これは `Graphs.bipartite_map(G)` を使用して計算できます。

# 例

```jldoctest V_motifs_nodes
julia> using Graphs

julia> G = SimpleGraph(5); add_edge!(G, 1, 4); add_edge!(G, 1, 5); add_edge!(G, 2, 4); add_edge!(G, 2, 5); add_edge!(G, 3, 4);

julia> V_motifs(G, 1, 2)
2

```
