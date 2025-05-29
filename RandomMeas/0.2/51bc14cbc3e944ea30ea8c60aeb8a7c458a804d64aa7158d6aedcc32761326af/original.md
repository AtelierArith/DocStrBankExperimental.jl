```
partial_transpose(shadow::AbstractShadow, subsystem::Vector{Int})
```

Compute the partial transpose of a shadow object over the specified subsystem(s). This operation is analogous to QuTiP's partial transpose method.

# Arguments

  * `shadow::AbstractShadow`: The shadow object for which the partial transpose is computed.
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) specifying the subsystem(s) over which to perform the transpose.

# Returns

A new shadow object that is the partial transpose of the input.

# Example

```julia
transposed_shadow = partial_transpose(shadow, [2, 4])
```
