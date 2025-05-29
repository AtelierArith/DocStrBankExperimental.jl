```
reduce_to_subsystem(
group::MeasurementGroup{T},
subsystem::Vector{Int}
```

)::MeasurementGroup{T} where T <: LocalMeasurementSetting

Reduce a `MeasurementGroup object (with`LocalUnitaryMeasurementSetting`) to a specified subsystem.

# Arguments

  * `group::MeasurementGroup{LocalUnitaryMeasurementSetting}`: The original measurement data object.
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) specifying the subsystem to retain.

# Returns

A new `MeasurementGroup` object corresponding to the specified subsystem.
