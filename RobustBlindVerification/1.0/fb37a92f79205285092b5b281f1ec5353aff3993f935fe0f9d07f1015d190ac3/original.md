````
get_number_qubits(resource::MBQCResourceState)

Retrieve the number of qubits in an MBQC resource state.

# Arguments
- `resource::MBQCResourceState`: An MBQC resource state containing the graph representation of the resource.

# Returns
The number of qubits in the resource state.

# Examples
```julia
# Create an MBQC resource state
graph = MBQCGraph(...)
flow = MBQCFlow(...)
angles = MBQCAngles(...)
resource = MBQCResourceState(graph, flow, angles)

# Get the number of qubits
num_qubits = get_number_qubits(resource)
```
````
