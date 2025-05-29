```
is_vertex_in_graph(resource::MBQCResourceState, novertex::Nothing)
```

Check if a vertex is present in the graph.

# Arguments

  * `resource::MBQCResourceState`: The MBQC resource state.
  * `novertex::Nothing`: The vertex to check.

# Returns

  * `true` if the vertex is present in the graph, `false` otherwise.

# Example

```julia
is_vertex_in_graph(resource, novertex) # Returns true if the vertex is present in the graph, false otherwise
```
