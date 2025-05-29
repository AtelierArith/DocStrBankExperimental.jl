```julia
struct MaximalIS{T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

最大独立集合は、[`IndependentSet`](@ref) 問題に非常に似た問題です。違いは、最大独立集合問題の解空間には、もう1つの頂点を追加することで拡張できる独立集合が含まれないことです。

## フィールド

  * `graph` は問題のグラフです。
  * `weights` は `graph` の頂点に関連付けられています。

## 例

以下の例では、4つの頂点を持つグラフ上で最大独立集合問題を定義します。`MaximalIS` 問題を定義するには、グラフと頂点に関連付けられた重みを指定する必要があります。重みは現在のバージョンではデフォルトで単位として設定されており、今後の開発で任意の正の重みに一般化される可能性があります。

```jldoctest
julia> using ProblemReductions, Graphs

julia> graph = SimpleGraph(Graphs.SimpleEdge.([(1, 2), (1, 3), (3, 4), (2, 3), (1, 4)]))
{4, 5} undirected simple Int64 graph

julia> problem = MaximalIS(graph)
MaximalIS{Int64, UnitWeight}(SimpleGraph{Int64}(5, [[2, 3, 4], [1, 3], [1, 2, 4], [1, 3]]), [1, 1, 1, 1])

julia> num_variables(problem)  # 自由度
4

julia> flavors(problem)
(0, 1)

julia> solution_size(problem, [0, 1, 0, 0])  # 独立集合とは異なり、この構成は有効な解ではありません
SolutionSize{Int64}(1, false)

julia> findbest(problem, BruteForce())
1-element Vector{Vector{Int64}}:
 [0, 1, 0, 1]
```
