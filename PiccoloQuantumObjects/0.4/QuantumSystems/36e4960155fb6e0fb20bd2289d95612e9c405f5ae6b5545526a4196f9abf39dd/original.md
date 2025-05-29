```
QuantumSystem <: AbstractQuantumSystem
```

A struct for storing quantum dynamics and the appropriate gradients.

# Fields

  * `H::Function`: The Hamiltonian function, excluding dissipation: a -> H(a).
  * `G::Function`: The isomorphic generator function, including dissipation, a -> G(a).
  * `∂G::Function`: The generator jacobian function, a -> ∂G(a).
  * `levels::Int`: The number of levels in the system.
  * `n_drives::Int`: The number of drives in the system.

# Constructors

  * QuantumSystem(H*drift::AbstractMatrix{<:Number}, H*drives::Vector{<:AbstractMatrix{<:Number}}; kwargs...)
  * QuantumSystem(H_drift::AbstractMatrix{<:Number}; kwargs...)
  * QuantumSystem(H_drives::Vector{<:AbstractMatrix{<:Number}}; kwargs...)
  * QuantumSystem(H::Function, n_drives::Int; kwargs...)
