```
error_probability(
    priors::AbstractVector,
    ρ_states::Vector{<:AbstractMatrix},
    Π::AbstractVector{<:AbstractMatrix}
) :: Float64
```

The probability of incorrectly distinguishing quantum states with the specifed POVM. This quantity is simply obtained as $P_{\text{Error}} = 1 - P_{\text{Success}}$.
