```julia
dsw(
    g::NoncommutativeGraphs.S0Graph,
    w::AbstractMatrix{<:Number};
    use_diag_optimization,
    eps,
    verbose
) -> NamedTuple{(:λ, :x, :Z), <:Tuple{Any, Any, Any}}

```

Compute weighted θ using theorem 14 of arxiv:2101.00162.

Returns optimal λ, x, and Z values in a named tuple. If `use_diag_optimization=true` (the default) then `x ⪰ w` and `x` is in the commutant of S₀.  By theorem 29 of arxiv:2101.00162, θ(g, w) = θ(g, x).
