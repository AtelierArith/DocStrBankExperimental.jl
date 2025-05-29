```
remove_edges(g::GNNGraph, edges_to_remove::AbstractVector{<:Integer})
remove_edges(g::GNNGraph, p=0.5)
```

指定されたエッジをGNNGraphから削除します。エッジのインデックスを指定するか、指定された確率でランダムにエッジを削除します。

# 引数

  * `g`: エッジが削除される入力グラフ。
  * `edges_to_remove`: 削除されるエッジのインデックスのベクター。この引数は最初のメソッドにのみ必要です。
  * `p`: 各エッジを削除する確率。この引数は2番目のメソッドにのみ必要で、デフォルトは0.5です。

# 戻り値

指定されたエッジが削除された新しいGNNGraph。

# 例

```julia
julia> using GNNGraphs

# GNNGraphを構築
julia> g = GNNGraph([1, 1, 2, 2, 3], [2, 3, 1, 3, 1])
GNNGraph:
  num_nodes: 3
  num_edges: 5
  
# 2番目のエッジを削除
julia> g_new = remove_edges(g, [2]);

julia> g_new
GNNGraph:
  num_nodes: 3
  num_edges: 4

# 確率0.5でエッジを削除
julia> g_new = remove_edges(g, 0.5);

julia> g_new
GNNGraph:
  num_nodes: 3
  num_edges: 2
```
