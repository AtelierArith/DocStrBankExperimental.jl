````
MBQCResourceState(graph, flow, angles)

Struct representing a resource state in MBQC.

# Parameters
- `graph`: An instance of `MBQCGraph` representing the underlying graph structure.
- `flow`: An instance of `MBQCFlow` representing the flow in the resource state.
- `angles`: An instance of `MBQCAngles` representing the angles associated with each vertex.

## Example
```julia
# Create an MBQCGraph
graph = MBQCGraph([1, 2, 3], [(1, 2), (2, 3)])

# Create an MBQCFlow
flow = MBQCFlow((1, 2) => 2, (2, 3) => 3)

# Create an MBQCAngles
angles = MBQCAngles([π/2, π/4, π/3])

# Create an MBQCResourceState
resource_state = MBQCResourceState(graph, flow, angles)
```
````
