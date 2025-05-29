```
random_orientation_dag(g)
```

ランダムな有向非巡回グラフを生成します。この関数は、単純なグラフと乱数生成器を引数として受け取ります。各方向性非巡回グラフがランダムに生成される確率は、元の有向グラフの構造に依存します。

DAGは有限のトポロジカル順序を持ちます。この順序は「order = randperm()」を介してランダムに生成されます。

# 例

```jldoctest
julia> using Graphs

julia> random_orientation_dag(complete_graph(10))
{10, 45} directed simple Int64 graph

julia> random_orientation_dag(star_graph(Int8(10)), seed=123)
{10, 9} directed simple Int8 graph
```
