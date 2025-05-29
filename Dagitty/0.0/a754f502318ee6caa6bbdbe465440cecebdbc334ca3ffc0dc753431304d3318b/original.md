```
drawdag(dag, locs_x, locs_y)
```

Draws dag with given locations of every node

# Examples

```julia
julia> g = DAG(:A => :C, :C => :B)
DAG: {3, 2} directed simple Int64 graph with labels [:A, :B, :C])

julia> drawdag(g, [0, 0, 1], [0, 1, 1])
```
