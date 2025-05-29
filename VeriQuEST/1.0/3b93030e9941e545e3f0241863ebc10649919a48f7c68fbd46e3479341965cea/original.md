```
assert_flow(flow_type, resource, vertex)
```

Check the validity of a flow in a resource graph.

Arguments:

  * `flow_type`: The type of flow to be checked.
  * `resource`: The resource state representing the graph.
  * `vertex`: The vertex to be checked.

This function performs several assertions to verify the flow:

  * Checks if the flow of the given vertex is in the vertex set of the graph.
  * Checks if the given vertex is in the neighborhood of the flow of the vertex.
  * Checks if the given vertex is less than or equal to the flow of the vertex.
  * Checks if all vertices in the neighborhood of the flow of the vertex are greater than or equal to the vertex.

# Examples

```julia
assert_flow(ForwardFlow(), resource, vertex) # Checks the validity of the forward flow
```
