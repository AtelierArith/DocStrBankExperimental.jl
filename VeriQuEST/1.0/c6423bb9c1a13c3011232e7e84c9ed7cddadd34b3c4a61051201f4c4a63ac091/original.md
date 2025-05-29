```
get_verified_flow(T, resource::MBQCResourceState)
```

Create a function that returns the verified flow output for a given vertex.

# Arguments

  * `T`: The flow graph.
  * `resource`: The MBQC resource state.

# Returns

A function `f` that takes a vertex as input and returns the verified flow output.

# Example

```julia
T = ForwardFlow()
resource = MBQCResourceState(...)
f = get_verified_flow(T, resource) # Returns a function that takes a vertex as input and returns the verified flow output
```
