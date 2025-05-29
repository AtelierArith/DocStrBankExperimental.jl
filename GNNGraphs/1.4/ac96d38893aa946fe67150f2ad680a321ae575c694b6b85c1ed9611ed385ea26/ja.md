```
add_edges(g::GNNGraph, s::AbstractVector, t::AbstractVector; [edata])
add_edges(g::GNNGraph, (s, t); [edata])
add_edges(g::GNNGraph, (s, t, w); [edata])
```

グラフ `g` にソースノード `s` とターゲットノード `t` を持つエッジを追加します。オプションで、エッジの重み `w` と新しいエッジの特徴 `edata` を渡すことができます。`g` と一部の基礎データを共有する新しいグラフを返します。

`s` または `t` にグラフに既に存在しないノードが含まれている場合、それらもグラフに追加されます。

# 例

```jldoctest
julia> s, t = [1, 2, 3, 3, 4], [2, 3, 4, 4, 4];

julia> w = Float32[1.0, 2.0, 3.0, 4.0, 5.0];

julia> g = GNNGraph((s, t, w))
GNNGraph:
  num_nodes: 4
  num_edges: 5

julia> add_edges(g, ([2, 3], [4, 1], [10.0, 20.0]))
GNNGraph:
  num_nodes: 4
  num_edges: 7
```

```jldoctest
julia> g = GNNGraph()
GNNGraph:
  num_nodes: 0
  num_edges: 0

julia> add_edges(g, [1,2], [2,3])
GNNGraph:
  num_nodes: 3
  num_edges: 2
```
