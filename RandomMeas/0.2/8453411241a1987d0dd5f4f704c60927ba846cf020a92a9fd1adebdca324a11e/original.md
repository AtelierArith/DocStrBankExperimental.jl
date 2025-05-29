```
get_trace_moment(ψ::Union{MPS, MPO}, k::Int, subsystem::Vector{Int}=collect(1:length(ψ)))
```

Compute the kth trace moment of the reduced density matrix for a given subsystem of a quantum state.

For a pure state (MPS) and when the subsystem is contiguous starting from site 1, the function computes the entanglement spectrum of the bipartition defined by the last site in `subsystem` and returns the kth moment of the squared Schmidt coefficients. Otherwise, the function reduces the state to the specified subsystem.

For k = 2 (purity), it returns the squared norm (which is equivalent to tr(ρ²)). For k > 2, it computes ρ^k via repeated application of the `apply` function (with a cutoff) and returns the trace of the resulting tensor.

# Arguments

  * `ψ::Union{MPS, MPO}`: The quantum state, represented as an MPS (for pure states) or MPO (for mixed states).
  * `k::Int`: The moment order to compute (must be an integer ≥ 1).
  * `subsystem::Vector{Int}` (optional): A vector of site indices (1-based) specifying the subsystem to retain. Defaults to all sites.

# Returns

A scalar (Float64) representing the kth trace moment of the reduced density matrix.

# Example

```julia
moment = get_trace_moment(ψ, 3, [1, 2, 3]; partial_transpose=false)
```
