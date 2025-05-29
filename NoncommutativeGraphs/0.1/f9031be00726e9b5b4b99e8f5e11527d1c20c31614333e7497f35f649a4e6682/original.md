```julia
dsw_schur2(
    g::NoncommutativeGraphs.S0Graph
) -> @NamedTuple{λ::Convex.AbstractExpr, w::Convex.AbstractExpr, Z::Convex.AbstractExpr}

```

Schur complement form of weighted θ from theorem 14 of arxiv:2101.00162, optimized for the case S₀ ≠ ℂI, at the cost of w being constrained to S₁ (the commutant of S₀).

Returns λ, w, and Z variables (for Convex.jl) in a named tuple.

See also: [`dsw_schur2`](@ref).
