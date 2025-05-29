```
holevo_bound(
    priors :: AbstractVector,
    ρ_states :: Vector{<:AbstractMatrix}
) :: Float64
```

The Holevo theorem places a bound on the [`mutual_information`](@ref) $I(X : Y) \leq \mathcal{X}$. It places a limit on the amount information that can be decoded from a set of quantum states. For a mixed state $\rho = \sum_i p_i \rho_i$ the Holevo bound $\mathcal{X}$ is

$$
\mathcal{X}  := S(\rho) - \sum_i p_i S(\rho_i)
$$

where $S(\rho)$ is the [`von_neumann_entropy`](@ref).

A `DomainError` is thrown  if:

  * `priors` does not satisfy [`is_probability_distribution`](@ref).
  * Any `ρ ∈ ρ_states` does not satisfy [`is_density_matrix`](@ref).
