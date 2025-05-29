```
compute_backward_flow(graph, forward_flow, vertex)
```

This function computes the backward flow of a given vertex in a graph.  It first finds the neighbors of the vertex and checks if the vertex is in the forward flow of any of its neighbors.  If it is not, the function returns 0.  If it is, the function finds the index of the vertex in the forward flow of its neighbors.  If the vertex is not in the flow of the neighbors, an error is thrown.  If there is more than one past vertex found, an error is thrown.  Otherwise, the function returns the first past vertex.

# Arguments

  * `graph`: The graph.
  * `forward_flow`: The forward flow function.
  * `vertex`: The vertex for which to compute the backward flow.

# Returns

  * The first past vertex if it exists, 0 otherwise.

# Examples

```julia
graph = Graph(5)
forward_flow = (n -> n + 1)
vertex = 3
backward_flow_vertex = compute_backward_flow(graph, forward_flow, vertex)
```
