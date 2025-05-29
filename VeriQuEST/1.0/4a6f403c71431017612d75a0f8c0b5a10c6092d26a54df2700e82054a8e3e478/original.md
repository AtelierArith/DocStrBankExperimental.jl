get*vertex*neighbours(resource::MBQCResourceState, vertex)

Retrieve the neighbors of a given vertex in an MBQC resource state.

# Arguments

  * `resource::MBQCResourceState`: An MBQC resource state containing the graph representation of the resource.
  * `vertex`: The vertex for which to retrieve the neighbors.

# Returns

An array of vertices representing the neighbors of the specified vertex.

# Examples

```julia
# Create an MBQC resource state
graph = MBQCGraph(...)
flow = MBQCFlow(...)
angles = MBQCAngles(...)
resource = MBQCResourceState(graph, flow, angles)

# Get the neighbors of a vertex
vertex = 1
neighbors = get_vertex_neighbours(resource, vertex)
```
