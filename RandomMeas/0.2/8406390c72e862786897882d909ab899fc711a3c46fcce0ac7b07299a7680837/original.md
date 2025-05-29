```
get_siteinds(ψ::Union{MPS, MPO})
```

Retrieve the site indices for a quantum state represented as an MPS or MPO.

# Arguments

  * `ψ`: The quantum state, which can be either a Matrix Product State (MPS) or a Matrix Product Operator (MPO).

# Returns

A vector of site indices corresponding to the quantum state `ψ`.

# Example

```julia
ξ = get_siteinds(ψ)
```
