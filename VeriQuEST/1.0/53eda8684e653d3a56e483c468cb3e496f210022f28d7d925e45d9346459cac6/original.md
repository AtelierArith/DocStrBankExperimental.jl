```
get_vertex_iterator(resource::MBQCResourceState)
```

Retrieve an iterator over the vertices in an MBQC resource state.

# Arguments

  * `resource::MBQCResourceState`: An MBQC resource state containing the graph representation of the resource.

# Returns

An iterator over the vertices of the resource state's graph.

# Examples

```julia
# Create an MBQC resource state
graph = MBQCGraph(...)
flow = MBQCFlow(...)
angles = MBQCAngles(...)
resource = MBQCResourceState(graph, flow, angles)

# Get the vertex iterator
vertex_iterator = get_vertex_iterator(resource)
```
