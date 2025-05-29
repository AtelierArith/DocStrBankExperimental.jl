```
get_corrections_one_neighbourhood_two_vertex_graph(resource::MBQCResourceState, vertex::Int64)
```

This function calculates the corrections needed for a two-vertex graph in a one-neighbourhood MBQC resource state.

# Arguments

  * `resource::MBQCResourceState`: The MBQC resource state.
  * `vertex::Int64`: The vertex in the graph.

# Returns

  * `corrections`: A tuple `(X=x_correction_vertex, Z=z_correction_vertices)` representing the corrections needed.

# Errors

  * Throws an error if the vertex is not in the graph.
  * Throws an error if the size of the graph is not 2.
  * Throws an error if the size of the vertex neighbour set is not 1.
  * Throws an error if neither the forward flow nor the backward flow of the vertex is in the graph.

# Examples

```julia
corrections = get_corrections_one_neighbourhood_two_vertex_graph(resource, vertex) # Returns the corrections needed for the given vertex
```
