```julia
struct SpinGlass{GT<:Graphs.AbstractGraph, T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

```
SpinGlass(graph::AbstractGraph, weights::AbstractVector)
SpinGlass(graph::SimpleGraph, J, h=zeros(nv(graph)))
```

スピンガラスは、ガラスのような挙動を示す無秩序な磁気システムの一種です。単純グラフ $G=(V, E)$ 上のシステムのハミルトニアンは次のように与えられます。

$$
H(G, \sigma) = \sum_{(i,j) \in E} J_{ij} \sigma_i \sigma_j + \sum_{i \in V} h_i \sigma_i
$$

ここで、$J_{ij} \in \mathbb{R}$ はスピン $i$ と $j$ の間の結合強度、$h_i \in \mathbb{R}$ はスピン $i$ にかかる外部場、$\sigma_i \in \{-1, 1\}$ はスピン変数です。解の構成は (0, 1) のバイナリ変数によって指定され、0 と 1 はそれぞれスピン -1 と 1 にマッピングされます。

この定義は、[`HyperGraph`](@ref) の場合にも自然に拡張されます：

$$
H(G, \sigma) = \sum_{e \in E} J_{e} \prod_k\sigma_k + \sum_{i \in V} h_i \sigma_i,
$$

ここで、$J_e$ はハイパーエッジ $e$ に関連する結合強度であり、積はハイパーエッジ内のすべてのスピンにわたります。

## フィールド

  * `graph` はグラフオブジェクトです。
  * `J` はエッジに関連する結合強度です。
  * `h` は頂点に関連する外部場です。

## 例

以下の例では、エッジに対する結合強度と頂点に対する外部場が与えられた4頂点グラフ上でスピンガラス問題を定義します。

```jldoctest
julia> using ProblemReductions, ProblemReductions.Graphs

julia> graph = SimpleGraph(Graphs.SimpleEdge.([(1, 2), (1, 3), (3, 4), (2, 3)]))
{4, 4} undirected simple Int64 graph

julia> J = [1, -1, 1, -1]  # 結合強度
4-element Vector{Int64}:
  1
 -1
  1
 -1

julia> h = [1, -1, -1, 1]  # 外部場
4-element Vector{Int64}:
  1
 -1
 -1
  1

julia> spinglass = SpinGlass(graph, J, h)  # スピンガラス問題を定義
SpinGlass{SimpleGraph{Int64}, Int64, Vector{Int64}}(SimpleGraph{Int64}(4, [[2, 3], [1, 3], [1, 2, 4], [3]]), [1, -1, 1, -1], [1, -1, -1, 1])

julia> num_variables(spinglass)  # 自由度
4

julia> flavors(spinglass)  # スピンのフレーバー、0 は上 (+1)、1 は下 (-1)
(0, 1)

julia> solution_size(spinglass, [1, 0, 0, 1])  # 構成のサイズ
SolutionSize{Int64}(-2, true)

julia> findbest(spinglass, BruteForce())  # ブルートフォースで問題を解く
1-element Vector{Vector{Int64}}:
 [1, 0, 1, 1]
```
