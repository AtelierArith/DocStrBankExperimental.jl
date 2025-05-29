```
get_verified_flow_output(T, resource, vertex)
```

Get the verified flow output for a given vertex in a MBQC resource state.

# Arguments

  * `T`: The type of flow, which must be either `ForwardFlow` or `BackwardFlow`.
  * `resource`: The MBQC resource state.
  * `vertex`: The vertex for which to get the verified flow output.

# Returns

  * If the flow output is a valid vertex in the neighborhood of the given vertex, it returns the verified flow output.
  * If the flow output is `Nothing`, it returns `nothing`.
  * If the flow type is neither `ForwardFlow` nor `BackwardFlow`, it throws an error.

# Examples

```julia
T = ForwardFlow()
resource = MBQCResourceState(...)
vertex = 1
output = get_verified_flow_output(T, resource, vertex) # Returns the verified flow output for the given vertex
```
