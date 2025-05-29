```
export_graph(filename, graph::GameGraph)
export_graph(filename, edges::Vector{Vector{Int}})
```

Export a graph to file. Format is simplest possible. On line `n` is listed the outgoing edges from node `n`, separated by spaces.
