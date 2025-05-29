```
node(dag, label)
```

DAG内のノードラベルを解決する：ノードラベルによって基になるグラフノードインデックスを返す

# 例

```jldoctest
julia> using Dagitty

julia> g = DAG(:A => :C, :C => :B)
DAG: {3, 2} directed simple Int64 graph with labels [:A, :B, :C])

julia> node(g, :C)
3
```
