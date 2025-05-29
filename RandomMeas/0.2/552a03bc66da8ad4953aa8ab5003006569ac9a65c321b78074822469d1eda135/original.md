```
get_trace_moments(ψ::Union{MPS, MPO}, k_vector::Vector{Int}, subsystem::Vector{Int}=collect(1:length(ψ)))
```

Compute a vector of trace moments for a quantum state `ψ` over a specified subsystem.

For each moment order `k` in `k_vector`, the function computes the kth trace moment of the reduced density matrix obtained by applying `reduce_to_subsystem(ψ, subsystem)`.

# Arguments

  * `ψ::Union{MPS, MPO}`: The quantum state, represented as an MPS (for pure states) or an MPO (for mixed states).
  * `k_vector::Vector{Int}`: A vector of integer moment orders (each ≥ 1) for which the trace moments are computed.
  * `subsystem::Vector{Int}` (optional): A vector of site indices (1-based) specifying the subsystem to consider. Defaults to all sites.

# Returns

A vector of scalars, each being the kth trace moment corresponding to the entries of `k_vector`.

# Example

```julia
moments = get_trace_moments(ψ, [1, 2, 3], [1, 2, 3])
```
