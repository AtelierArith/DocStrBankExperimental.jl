```
get_overlap(
    group_1::MeasurementGroup,
    group_2::MeasurementGroup,
    subsystem::Vector{Int} = collect(1:group_1.N);
    apply_bias_correction::Bool = false
)
```

Compute the overlap of two quantum states from measurement data by averaging the overlap of measurement results.

# Arguments

  * `group_1::MeasurementGroup`: Measurement data for the first state.
  * `group_2::MeasurementGroup`: Measurement data for the second state.
  * `subsystem::Vector{Int}` (optional): A vector of site indices specifying the subsystem to retain. Defaults to the full system.
  * `apply_bias_correction::Bool` (optional): Whether to apply bias correction for the overlap. Defaults to `false`.

# Returns

  * The computed overlap (or purity if `group_1 == group_2` and bias correction is applied).
