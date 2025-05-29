Struct to represent a labeled graph. Unique symbols are created for each vertex if none are provided and remain unaltered during the lifetime of the graph.

# Example

```julia-repl
julia> g = LabeledGraph()
LabeledGraph({0, 0} undirected simple Int64 graph, Symbol[])

julia> add_vertex!(g, :a_vertex_label)
1-element Array{Symbol,1}:
 :a_vertex_label

julia> g.labels[1]
:a_vertex_label
```
