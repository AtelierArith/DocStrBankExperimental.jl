```
function mincost_flow(g::AbstractGraph,
		node_demand::AbstractVector,
		edge_capacity::AbstractMatrix,
		edge_cost::AbstractMatrix,
		optimizer;
		edge_demand::Union{Nothing,AbstractMatrix} = nothing,
		source_nodes = (),
		sink_nodes = ()
		)
```

有向グラフ `g` 上でフローを見つけ、各ノードで `node_demand` を満たし、各エッジの `edge_capacity` 制約を守りながら `dot(edge_cost, flow)` を最小化します。

スパースフローマトリックスを返します。flow[i,j] は (i,j) アークのフローに対応します。

# 引数

  * `g` は有向 `LightGraphs.AbstractGraph` です。
  * `node_demand` はノードの需要値のベクトルで、ソースの場合は負、シンクノードの場合は正、その他のノードではゼロである必要があります。
  * `edge_capacity::AbstractMatrix` は各アークのフローの上限を設定します。
  * `edge_cost::AbstractMatrix` は各アークの単位フローあたりのコストです。
  * `optimizer` は `Clp.Optimizer` や `() -> Clp.Optimizer()` のようなオプティマイザコンストラクタで、`JuMP.Model` の構築時に渡されます。

# キーワード引数

  * `edge_demand::Union{Nothing,AbstractMatrix}`: エッジに対して最小フローを要求するか、何もしない。
  * `source_nodes` ノードのネットフローがノードの需要を超えることが許可されるソースのコレクションで、デフォルトは空のタプルです。
  * `sink_nodes` ノードのネットフローがノードの需要を下回ることが許可されるシンクのコレクションで、デフォルトは空のタプルです。

`source_nodes` と `sink_nodes` は、ノードフローが `node_demand` に明示的に設定されていない場合にのみ必要です。

### 使用例:

```julia
julia> import LightGraphs
julia> const LG = LightGraphs
julia> using LightGraphsFlows: mincost_flow
julia> import Clp # お好みの LP ソルバーをここで使用
julia> using SparseArrays: spzeros
julia> g = LG.DiGraph(6) # フローグラフを作成
julia> LG.add_edge!(g, 5, 1)
julia> LG.add_edge!(g, 5, 2)
julia> LG.add_edge!(g, 3, 6)
julia> LG.add_edge!(g, 4, 6)
julia> LG.add_edge!(g, 1, 3)
julia> LG.add_edge!(g, 1, 4)
julia> LG.add_edge!(g, 2, 3)
julia> LG.add_edge!(g, 2, 4)
julia> cost = zeros(6,6)
julia> cost[1,3] = 10
julia> cost[1,4] = 5
julia> cost[2,3] = 2
julia> cost[2,4] = 2
julia> demand = spzeros(6)
julia> demand[5] = -2
julia> demand[6] = 2
julia> capacity = ones(6,6)
julia> flow = mincost_flow(g, demand, capacity, cost, Clp.Optimizer)
```
