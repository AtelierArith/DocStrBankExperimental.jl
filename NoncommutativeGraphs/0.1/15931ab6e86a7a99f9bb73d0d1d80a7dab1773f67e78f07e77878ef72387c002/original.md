```julia
dsw_via_complement(
    g::NoncommutativeGraphs.S0Graph,
    w::AbstractMatrix{<:Number};
    use_diag_optimization,
    eps,
    verbose
) -> NamedTuple{(:λ, :x, :y, :Z), <:NTuple{4, Any}}

```

Compute weighted θ via the complement graph, using theorem 29 of arxiv:2101.00162.

θ(S, w) = max{ tr(w x) : x ⪰ 0, y = Ψ(x), θ(Sᶜ, y) ≤ 1 }

Returns optimal λ, x, y, and Z in a named tuple.

If w is in the commutant of S₀ then the weights w and y saturate the inequality in theorem 32 of arxiv:2101.00162.
