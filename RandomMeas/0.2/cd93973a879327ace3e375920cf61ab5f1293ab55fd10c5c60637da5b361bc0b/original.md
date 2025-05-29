```
partial_trace(shadow::AbstractShadow, subsystem::Vector{Int}; assume_unit_trace::Bool=false)
```

Compute the partial trace of a shadow object over the complement of the specified subsystem.

# Arguments

  * `shadow::AbstractShadow`: The shadow object.
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) specifying the subsystem to retain.
  * `assume_unit_trace::Bool` (optional): If `true`, assumes the shadow has unit trace (default: `false`).   This can speed up the calculation for factorized shadows (as the trace of "traced out" qubits is not computed)/

# Returns

A new shadow object reduced to the specified subsystem.

# Example

```julia
reduced_shadow = partial_trace(shadow, [1, 3])
```
