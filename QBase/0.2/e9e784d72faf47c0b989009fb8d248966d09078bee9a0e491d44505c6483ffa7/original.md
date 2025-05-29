```
success_probability(
    priors::AbstractVector,
    states::Vector{<:AbstractMatrix},
    Π::Vector{<:AbstractMatrix}
) :: Float64
```

The probability of correctly distinguishing quantum states with the specifed POVM:

$$
P_{\text{Success}} = \sum_{i=1}^n p_i \text{Tr}[\Pi_i \rho_i].
$$

The number of states must match the number POVMs.
