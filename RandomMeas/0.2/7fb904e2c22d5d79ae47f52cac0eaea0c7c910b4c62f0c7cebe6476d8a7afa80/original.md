```
get_purity(group::Measurementgroup, subsystem::Vector{Int} = collect(1:group.N))
```

Compute the purity of a quantum state from measurement data by averaging the overlap of measurement results.

# Arguments

  * `group::MeasurementGroup`: Measurement data containing the results and settings of randomized measurements.
  * `subsystem::Vector{Int}` (optional): A vector of site indices specifying the subsystem to retain. Defaults to the full system.

# Returns

  * The computed purity for the specified subsystem.
