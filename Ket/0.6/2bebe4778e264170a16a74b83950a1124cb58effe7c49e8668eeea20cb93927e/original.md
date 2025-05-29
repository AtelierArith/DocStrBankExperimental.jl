```
discrimination_min_error(
    ρ::Vector{<:AbstractMatrix},
    q::Vector{<:Real} = fill(1/length(ρ), length(ρ));
    verbose = false,
    dualize = false,
    solver = Hypatia.Optimizer
)
```

Computes the minimum-error probability of discriminating a vector of states `ρ` with probabilities `q`, along with the optimal POVM. `q` is assumed uniform if omitted.
