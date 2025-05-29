```julia
mutable struct BipartiteGraph{I<:Integer, M} <: Graphs.AbstractGraph{I<:Integer}
```

2つの、可能性のある異なる、頂点の集合（ソースと依存関係）間の二部グラフの表現。ソース頂点を `1:N₁` とラベル付けし、それらが依存する頂点に（`1:N₂` とラベル付けして）マッピングします。

# フィールド

  * `ne`
  * `fadjlist`
  * `badjlist`
  * `metadata`

# 例

```julia
using ModelingToolkit

ne = 4
srcverts = 1:4
depverts = 1:2

# 6つのソース頂点
fadjlist = [[1],[1],[2],[2],[1],[1,2]]

# 依存する2つの頂点
badjlist = [[1,2,5,6],[3,4,6]]

bg = BipartiteGraph(7, fadjlist, badjlist)
```
