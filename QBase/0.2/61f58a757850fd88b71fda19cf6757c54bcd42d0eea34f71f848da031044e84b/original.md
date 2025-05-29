```
mutual_information(
    priors :: AbstractVector,
    ρ_states :: Vector{<:AbstractMatrix},
    Π :: AbstractVector
) :: Float64
```

Computes the classical mutual information for a quantum state and measurement encoding and decoding. The conditional probabilities are obtained from quantum states and measurements using [`measure`](@ref).

A `DomainError` is thrown if:

  * `priors` does not satisfy [`is_probability_distribution`](@ref).
  * Any `ρ ∈ ρ_states` does not satisfy [`is_density_matrix`](@ref).
  * `Π` does not satisfy [`is_povm`](@ref).
