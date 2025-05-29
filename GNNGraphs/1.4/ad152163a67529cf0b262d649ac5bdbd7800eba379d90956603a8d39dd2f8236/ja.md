```
get_graph_type(g::GNNGraph)
```

グラフ `g` の基盤となる表現をシンボルとして返します。

可能な値は次のとおりです：

  * `:coo`: 座標リスト表現。グラフはベクトルのタプル `(s, t, w)` として保存され、ここで `s` と `t` はエッジのソースノードとターゲットノード、`w` はエッジの重みです。
  * `:sparse`: スパース行列表現。グラフは重み付き隣接行列を表すスパース行列として保存されます。
  * `:dense`: 密行列表現。グラフは重み付き隣接行列を表す密行列として保存されます。

GNNGraphs.jl のグラフコンストラクタのデフォルト表現は `:coo` です。基盤となる表現は `g.graph` フィールドを通じてアクセスできます。

[`GNNGraph`](@ref) も参照してください。

# 例

GNNGraphs.jl のグラフコンストラクタのデフォルト表現は `:coo` です。

```jldoctest
julia> g = rand_graph(5, 10)
GNNGraph:
  num_nodes: 5
  num_edges: 10

julia> get_graph_type(g)
:coo
```

`GNNGraph` コンストラクタは、異なる表現を持つグラフを作成するためにも使用できます。

```jldoctest
julia> g = GNNGraph([2,3,5], [1,2,4], graph_type=:sparse)
GNNGraph:
  num_nodes: 5
  num_edges: 3

julia> g.graph
5×5 SparseArrays.SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 ⋅  ⋅  ⋅  ⋅  ⋅
 1  ⋅  ⋅  ⋅  ⋅
 ⋅  1  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  1  ⋅

julia> get_graph_type(g)
:sparse

julia> gcoo = GNNGraph(g, graph_type=:coo);

julia> gcoo.graph
([2, 3, 5], [1, 2, 4], [1, 1, 1])
```
