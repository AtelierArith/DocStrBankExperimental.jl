```
V_motifs(G::Graphs.SimpleGraph; membership::Vector=Graphs.bipartite_map(G), layer::Symbol=:bottom)
```

グラフ `G` の特定の層における V-モチーフの出現回数をカウントします。

*注意*: グラフの二部性は明示的にはチェックされません。

# 引数

  * `membership`: グラフの二部マッピング。これは `Graphs.bipartite_map(G)` を使用して計算できます。
  * `layer`: 層は `layer=:bottom` または `layer=:top` を渡すことで指定できます。層のメンバーシップはグラフの二部マップによって決定されます。

# 例

```jldoctest V_motifs_bipartite
julia> using Graphs

julia> G = SimpleGraph(5); add_edge!(G, 1, 4); add_edge!(G, 2, 4); add_edge!(G, 3, 4); add_edge!(G, 3, 5);

julia> V_motifs(G, layer=:bottom)
3

```

```jldoctest V_motifs_bipartite
julia> V_motifs(G, layer=:top)
1

```
