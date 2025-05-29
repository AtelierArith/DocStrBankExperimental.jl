```
get_XEB(ψ::MPS, measurement_data::MeasurementData)
```

Return the linear cross-entropy for the measurement results in `measurement_data`, with respect to a theory state `ψ`.

# Arguments:

  * `ψ::MPS`: The theoretical state to compare against.
  * `measurement_data::MeasurementData`: The measurement data object containing results and settings.

# Returns:

The linear cross-entropy as a `Float64`.
