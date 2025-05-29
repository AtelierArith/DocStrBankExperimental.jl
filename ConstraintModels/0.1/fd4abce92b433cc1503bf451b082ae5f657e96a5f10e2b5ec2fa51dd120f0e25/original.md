```
mincut(graph::AbstractMatrix{T}; source::Int, sink::Int, interdiction::Int = 0) where T <: Number
```

Compute the minimum cut of a graph.

# Arguments:

  * `graph`: Any matrix <: AbstractMatrix that describes the capacities of the graph
  * `source`: Id of the source node; must be set
  * `sink`: Id of the sink node; must be set
  * `interdiction`: indicates the number of forbidden links
