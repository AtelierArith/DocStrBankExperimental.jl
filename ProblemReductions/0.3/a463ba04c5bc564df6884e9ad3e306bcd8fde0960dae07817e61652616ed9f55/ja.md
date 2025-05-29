```julia
struct MaxCut{T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

Max Cut問題は重み付きグラフ上で定義されます。目標は、2つの集合に頂点を分割し、2つの集合間の辺の重みの合計を最大化することです。

## 位置引数

  * `graph` は問題のグラフです。
  * `weights` は `graph` の辺に関連付けられています。`weights` が `edges(graph)` の辺と同じ順序であることを確認する必要があります。

## 例

以下の例では、3つの頂点と辺の重み `[1,2,3]` を持つ完全グラフ上でMax Cut問題を解決します。

```jldoctest
julia> using ProblemReductions, Graphs

julia> g = complete_graph(3)
{3, 3} undirected simple Int64 graph

julia> maxcut = MaxCut(g,[1,2,3]) # 辺の重みを指定
MaxCut{Int64, Vector{Int64}}(SimpleGraph{Int64}(3, [[2, 3], [1, 3], [1, 2]]), [1, 2, 3])

julia> mc = set_weights(maxcut, [2,1,3]) # 重みを設定し、新しいインスタンスを取得
MaxCut{Int64, Vector{Int64}}(SimpleGraph{Int64}(3, [[2, 3], [1, 3], [1, 2]]), [2, 1, 3])


julia> num_variables(maxcut) # 頂点の数を返す
3

julia> flavors(maxcut) # 頂点のフレーバーを返す
(0, 1)

julia> solution_size(maxcut, [0,1,0]) # 構成のサイズを返す
SolutionSize{Int64}(4, true)

julia> findbest(maxcut, BruteForce()) # 最良の構成を見つける
2-element Vector{Vector{Int64}}:
 [1, 1, 0]
 [0, 0, 1]
```
