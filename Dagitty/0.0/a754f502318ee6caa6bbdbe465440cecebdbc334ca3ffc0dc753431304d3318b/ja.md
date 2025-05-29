```
drawdag(dag, locs_x, locs_y)
```

指定された各ノードの位置でdagを描画します

# 例

```julia
julia> g = DAG(:A => :C, :C => :B)
DAG: {3, 2} directed simple Int64 graph with labels [:A, :B, :C])

julia> drawdag(g, [0, 0, 1], [0, 1, 1])
```
