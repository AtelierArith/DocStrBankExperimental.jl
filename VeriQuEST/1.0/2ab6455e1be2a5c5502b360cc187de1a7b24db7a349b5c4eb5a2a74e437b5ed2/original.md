```
get_measurement_outcome_iterator(resource::MBQCResourceState)
```

Returns an iterator that generates indices for measuring the vertices of a MBQC resource state.

# Arguments

  * `resource::MBQCResourceState`: The MBQC resource state.

# Returns

An iterator that generates indices for measuring the vertices of the resource state.

# Example

```julia
iterator = get_measurement_outcome_iterator(resource) # Returns an iterator that generates indices for measuring the vertices of the resource
```
