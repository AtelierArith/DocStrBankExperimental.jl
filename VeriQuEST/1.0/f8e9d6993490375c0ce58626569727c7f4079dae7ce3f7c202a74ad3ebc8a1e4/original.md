```
get_angle(resource::MBQCResourceState, AngleType, vertex)
```

Returns the angle of a specific vertex from a given `MBQCResourceState` and `AngleType`.

# Arguments

  * `resource`: An `MBQCResourceState` from which to extract the angle.
  * `AngleType`: The type of angle to be extracted.
  * `vertex`: The vertex for which to extract the angle.

# Examples

```julia
angle = get_angle(resource, SecretAngles(), vertex) # Returns the angle of the specified vertex
```
