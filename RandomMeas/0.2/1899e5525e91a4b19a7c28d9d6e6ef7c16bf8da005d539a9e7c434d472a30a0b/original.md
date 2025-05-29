```
reduce_to_subsystem(ψ::MPS, subsystem::Vector{Int64})
```

Compute the reduced density matrix for a pure state represented by the MPS `ψ` over the specified subsystem.

This function first constructs the density matrix by taking the outer product of `ψ` with itself, and then applies the MPO version of `reduce_to_subsystem` to obtain the reduced density matrix for the sites specified in `subsystem`.

# Arguments

  * `ψ::MPS`: A Matrix Product State representing a pure quantum state.
  * `subsystem::Vector{Int64}`: A vector of site indices (1-based) specifying the subsystem to retain.

# Returns

An MPO representing the reduced density matrix over the specified subsystem.

# Example

```julia
ρ_sub = reduce_to_subsystem(ψ, [2, 3])
```
