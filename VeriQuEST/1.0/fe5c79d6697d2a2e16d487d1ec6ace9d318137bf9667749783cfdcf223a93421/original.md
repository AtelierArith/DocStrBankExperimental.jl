```
separate_each_color(g::Graphs.Coloring{Int64})
```

This function extracts from a `Graphs.Coloring{Int64}` and returns a `Vector{Vector{Int64}}`.  Once a coloring is selected, a vector of integers will result where:

  * 1 represents a Dummy vertex
  * 2 represents a Trap

# Arguments

  * `g::Graphs.Coloring{Int64}`: The graph coloring object.

# Examples

`julia g = Graphs.grid_graph((5,5)) coloring = Graphs.greedy_color(g) separate_each_color(coloring)``
