```
is_vertex_in_graph(resource::MBQCResourceState, vertex::Int64)
```

Check if a vertex is present in a graph.

# Arguments

  * `resource::MBQCResourceState`: The MBQC resource state.
  * `vertex::Int64`: The vertex to check.

# Returns

  * `Bool`: `true` if the vertex is present in the graph, `false` otherwise.

# Example

```julia
is_vertex_in_graph(resource, vertex) # Returns true if the vertex is present in the graph, false otherwise
```
