```
get_edge_iterator(resource::MBQCResourceState)
```

Retrieve an iterator over the edges in an MBQC resource state.

# Arguments

  * `resource::MBQCResourceState`: An MBQC resource state containing the graph representation of the resource.

# Returns

An iterator over the edges of the resource state's graph.

# Examples

```julia
# Create an MBQC resource state
graph = MBQCGraph(...)
flow = MBQCFlow(...)
angles = MBQCAngles(...)
resource = MBQCResourceState(graph, flow, angles)

# Get the edge iterator
edge_iterator = get_edge_iterator(resource)
```
