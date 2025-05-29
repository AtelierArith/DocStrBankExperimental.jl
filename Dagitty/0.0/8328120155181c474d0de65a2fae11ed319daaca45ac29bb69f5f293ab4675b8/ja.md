```
DAG
```

フィールドを持つ構造体：

  * `graph::SimpleDiGraph` - 基本となる有向グラフ
  * `labels::Vector{Symbol}` - 各ノードのラベルのベクター

`Pair{Symbol, Symbol}` のリストを渡すことで構築できます。

# 例

```jldoctest
julia> using Dagitty

julia> g = DAG(:A => :B)
DAG: {2, 1} directed simple Int64 graph with labels [:A, :B])

julia> g.graph
{2, 1} directed simple Int64 graph

julia> g.labels
2-element Vector{Symbol}:
 :A
 :B

julia> g = DAG(:A => :A)
ERROR: DAGHasLoops()
```
