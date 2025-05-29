```
partial_trace(shadow::FactorizedShadow, subsystem::Vector{Int}; assume_unit_trace::Bool = false)
```

Compute the partial trace of a `FactorizedShadow` object over the complement of the specified subsystem.

# Arguments

  * `shadow::FactorizedShadow`: The factorized shadow to compute the partial trace for.
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) specifying the subsystem to retain.
  * `assume_unit_trace::Bool` (optional): If `true`, assumes all traced-out tensors have unit trace and skips explicit computation (default: `false`).

# Returns

A new `FactorizedShadow` object reduced to the specified subsystem.

# Notes

  * If `assume_unit_trace` is `true`, avoids explicit trace computation for efficiency.
  * If `assume_unit_trace` is `false`, computes the traces of all tensors outside the subsystem and multiplies their product into the remaining tensors.
  * Issues a warning if the trace product deviates significantly from 1 when `assume_unit_trace` is `false`.
