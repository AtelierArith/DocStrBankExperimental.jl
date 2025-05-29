```
reduce_to_subsystem(ρ::MPO, subsystem::Vector{Int64})
```

Compute the reduced density matrix (as an MPO) for a specified subsystem.

# Arguments

  * `ρ::MPO`: A Matrix Product Operator representing the full density matrix.
  * `subsystem::Vector{Int64}`: A vector of site indices (1-based) specifying the subsystem to retain.

# Returns

An MPO representing the reduced density matrix over the sites specified in `subsystem`.

# Example

```julia
ρ_reduced = reduce_to_subsystem(ρ, [2, 3])
```
