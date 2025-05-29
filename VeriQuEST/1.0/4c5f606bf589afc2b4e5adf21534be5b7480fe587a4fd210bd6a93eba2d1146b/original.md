```
get_size_measurement_vector(resource::MBQCResourceState)::Int64
```

Get the size of the measurement vector for a given `MBQCResourceState`.

# Arguments

  * `resource::MBQCResourceState`: The resource state for which to calculate the measurement vector size.

# Returns

  * `Int64`: The size of the measurement vector.

# Examples

```julia
size = get_size_measurement_vector(resource) # Returns the size of the measurement vector
```
