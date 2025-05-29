```
guesswork_lower_bound(
    p::AbstractVector{T},
    ρBs::AbstractVector{<:AbstractMatrix};
    solver,
    c = T[1:length(p)..., 10_000],
    verbose::Bool = false,
)
```

See [`guesswork`](@ref) for the meaning of the arguments. Computes a lower bound to the optimal expected number of guesses by solving a relaxed version of the primal SDP. For `J` states, only needs `J^2` PSD variables subject to two linear constraints.
