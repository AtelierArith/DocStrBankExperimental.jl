```julia
struct IndependentSet{GT<:Graphs.AbstractGraph, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

```
IndependentSet(graph::AbstractGraph, weights::AbstractVector=UnitWeight(nv(graph))) -> IndependentSet
```

独立集合は、無向グラフにおける頂点の部分集合であり、集合内のすべての頂点が辺で接続されていない（または隣接していない）ことを意味します。最大独立集合問題は、最大の頂点数を持つ独立集合を見つけることであり、これはNP完全問題です。グラフを$G=(V, E)$とし、$w_v$を頂点$v$の重みとします。独立集合問題のエネルギーベースモデルは次のようになります：

$$
H(G, \mathbf{n}) = - \sum_{v \in V} w_v n_v + \sum_{(u, v) \in E} n_u n_v
$$

ここで、$n_v$は独立集合内の頂点の数を表し、すなわち、$n_v = 1$は$v$が独立集合に含まれる場合、$n_v = 0$はそうでない場合です。独立集合のサイズが大きいほど、エネルギーは低くなります。

## フィールド

  * `graph::AbstractGraph`: 問題のグラフ。
  * `weights::AbstractVector`: `graph`の頂点に関連付けられた重み。デフォルトは`UnitWeight(nv(graph))`です。

## 例

以下の例では、4つの頂点を持つグラフ上で独立集合問題を定義します。`IndependentSet`問題を定義するには、グラフと頂点に関連付けられた重みを指定する必要があります。現在のバージョンでは重みは単位として設定されており、任意の正の重みに一般化される可能性があります。

```jldoctest
julia> using ProblemReductions, Graphs

julia> graph = SimpleGraph(Graphs.SimpleEdge.([(1, 2), (1, 3), (3, 4), (2, 3)]))
{4, 4} 無向単純 Int64 グラフ

julia> IS = IndependentSet(graph)
IndependentSet{SimpleGraph{Int64}, Int64, UnitWeight}(SimpleGraph{Int64}(4, [[2, 3], [1, 3], [1, 2, 4], [3]]), [1, 1, 1, 1])

julia> num_variables(IS)  # 自由度
4

julia> flavors(IS)  # 頂点のフレーバー
(0, 1)

julia> solution_size(IS, [1, 0, 0, 1]) # 正のサンプル: -(サイズ)の独立集合
SolutionSize{Int64}(2, true)

julia> solution_size(IS, [0, 1, 1, 0]) # 負のサンプル: 0
SolutionSize{Int64}(2, false)

julia> findbest(IS, BruteForce())  # ブルートフォースで問題を解く
2-element Vector{Vector{Int64}}:
 [1, 0, 0, 1]
 [0, 1, 0, 1]
```
