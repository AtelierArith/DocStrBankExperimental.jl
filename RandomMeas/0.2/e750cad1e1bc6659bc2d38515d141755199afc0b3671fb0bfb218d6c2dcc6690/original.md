```
get_fidelity(
    group_1::MeasurementGroup,
    group_2::MeasurementGroup,
    subsystem::Vector{Int} = collect(1:group_1.N)
)
```

Compute the fidelity of two quantum states Tr(ρ1 ρ2)/SROOT(Tr(ρ1^2),Tr(ρ2^2)) from measurement data by averaging the overlap of measurement results.

# Arguments

  * `group_1::MeasurementGroup`: Measurement data for the first state.
  * `group_2::MeasurementGroup`: Measurement data for the second state.
  * `subsystem::Vector{Int}` (optional): A vector of site indices specifying the subsystem to retain. Defaults to the full system.

# Returns

  * The computed fidelity.
