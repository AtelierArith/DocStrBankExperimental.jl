```
get_angles(resource::MBQCResourceState, ::SecretAngles)
```

Returns the secret angles from a given `MBQCResourceState`.

# Arguments

  * `resource`: An `MBQCResourceState` from which to extract the secret angles.

# Examples

```julia
angles = get_angles(resource, SecretAngles()) # Returns the secret angles of the resource
```
