```
mixed_state(
    priors :: Probabilities,
    states :: Vector{<:State};
    atol=ATOL :: Float64
) :: State
```

Constructs the statistical mixture (weighted average) of quantum states. This method can also be used `Vector` and `Matrix` types which satisfy the requirements of [`is_probability_distribution`](@ref) and [`is_density_matrix`](@ref) respectively.

```julia
mixed_state(
    priors :: AbstractVector,
    states :: Vector{<:AbstractMatrix}
) :: State
```

A `DomainError` is thrown if the provided `Vector`s of `priors` or `states` do not satisfy their respective requirements.
