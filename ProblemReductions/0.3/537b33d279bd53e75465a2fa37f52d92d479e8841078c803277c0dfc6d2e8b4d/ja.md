```julia
struct Coloring{K, T, WT<:AbstractArray{T, 1}, OBJ} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

```
Coloring{K}(graph; weights=UnitWeight(nv(graph)), use_constraints::Bool=false)
```

頂点彩色問題（Coloring）は単純グラフ上で定義されます。k種類の色が与えられたとき、隣接する2つの頂点が同じ色を共有しないように、グラフ上のすべての頂点に色を付けることができるかどうかを判断する必要があります。

## フィールド

  * `graph` は問題のグラフです。
  * `weights` は `graph` の辺に関連付けられており、デフォルトは `UnitWeight(ne(graph))` です。

## 例

Coloring問題を初期化するには、まずグラフを定義し、色の数を決定する必要があります。

```jldoctest
julia> using ProblemReductions, Graphs

julia> g = smallgraph(:petersen) # 単純グラフを定義、例としてpetersenを使用
{10, 15} undirected simple Int64 graph

julia> coloring = Coloring{3}(g)  # 3色
Coloring{3, Int64, UnitWeight, ProblemReductions.EXTREMA}(SimpleGraph{Int64}(15, [[2, 5, 6], [1, 3, 7], [2, 4, 8], [3, 5, 9], [1, 4, 10], [1, 8, 9], [2, 9, 10], [3, 6, 10], [4, 6, 7], [5, 7, 8]]), [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1])

julia> variables(coloring)
1:10

julia> flavors(coloring)
(0, 1, 2)

julia> is_vertex_coloring(coloring.graph,[1,2,3,1,3,2,1,2,3,1]) #ランダムな割り当て
false
```
