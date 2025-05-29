```julia
struct DominatingSet{GT<:Graphs.AbstractGraph, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

```
DominatingSet(graph::AbstractGraph, weights::AbstractVector=UnitWeight(ne(graph))) -> DominatingSet
```

支配集合は、無向グラフの頂点の部分集合であり、集合内のすべての頂点が支配集合に含まれるか、その一次近傍に含まれることを意味します。支配集合問題は、最小の頂点数を持つ支配集合を見つけることです。

## フィールド

  * `graph` は問題のグラフです。
  * `weights::AbstractVector`: `graph` の頂点に関連付けられた重み。デフォルトは `UnitWeight(nv(graph))` です。

## 例

以下の例では、5つの頂点を持つパスグラフ上で支配集合問題を定義します。`DominatingSet` 問題を定義するには、グラフと頂点に関連付けられた重みを指定する必要があります。現在のバージョンでは重みはデフォルトで単位に設定されており、今後の開発で任意の正の重みに一般化される可能性があります。

```jldoctest
julia> using ProblemReductions, Graphs

julia> graph = path_graph(5)
{5, 4} undirected simple Int64 graph

julia> DS = DominatingSet(graph)
DominatingSet{SimpleGraph{Int64}, Int64, UnitWeight}(SimpleGraph{Int64}(4, [[2], [1, 3], [2, 4], [3, 5], [4]]), [1, 1, 1, 1, 1])

julia> variables(DS)  # 自由度
1:5

julia> flavors(DS)  # 頂点のフレーバー
(0, 1)

julia> solution_size(DS, [0, 1, 0, 1, 0]) # 正のサンプル: 支配集合の (サイズ)
SolutionSize{Int64}(2, true)

julia> solution_size(DS, [0, 1, 1, 0, 0]) # 負のサンプル: 頂点の数
SolutionSize{Int64}(2, false)

julia> findbest(DS, BruteForce())  # ブルートフォースで問題を解く
3-element Vector{Vector{Int64}}:
 [1, 0, 0, 1, 0]
 [0, 1, 0, 1, 0]
 [0, 1, 0, 0, 1]
```
