```
assert_flow(::BackwardFlow, resource::MBQCResourceState, vertex::Int64)
```

Asserts the properties of a backward flow in a MBQC resource state.

Arguments:

  * `::BackwardFlow`: The backward flow type.
  * `resource::MBQCResourceState`: The MBQC resource state.
  * `vertex::Int64`: The vertex to be checked.

The function checks the following properties of the backward flow:

1. The flow of the given vertex is in the vertex set of the resource state.
2. The given vertex is in the neighborhood of the flow of the given vertex.
3. The given vertex is less than or equal to all vertices in the neighborhood of the flow of the given vertex.

Throws an error with an appropriate message if any of the properties are violated.

# Examples

```julia
assert_flow(BackwardFlow(), resource, vertex) # Asserts the properties of the backward flow
```
