```
reduce_to_subsystem(settings, subsystem)
```

Reduce a `LocalMeasurementSetting` object to a specified subsystem.

# Arguments:

  * `settings::LocalMeasurementSetting`: The original measurement settings object.
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) specifying the subsystem to retain.

# Returns:

  * A new `LocalMeasurementSetting` object corresponding to the specified subsystem.

# Example:

```julia
reduced_setting = reduce_to_subsystem(full_setting, [1, 3])
```
