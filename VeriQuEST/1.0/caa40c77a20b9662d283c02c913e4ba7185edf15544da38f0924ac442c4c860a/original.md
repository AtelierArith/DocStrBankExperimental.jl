```
get_stop_start_vertices(resource::MBQCResourceState)
```

Get the start and stop vertices for a given `MBQCResourceState`.

# Arguments

  * `resource::MBQCResourceState`: The MBQC resource state.

# Returns

  * `Tuple{Int64, Int64}`: A tuple containing the start and stop vertices.

# Example

```julia
start, stop = get_stop_start_vertices(resource) # Returns the start and stop vertices
```
