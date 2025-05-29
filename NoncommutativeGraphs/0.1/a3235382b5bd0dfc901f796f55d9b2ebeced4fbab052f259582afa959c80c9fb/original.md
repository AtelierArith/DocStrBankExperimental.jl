```julia
dsw_schur(
    g::NoncommutativeGraphs.S0Graph
) -> @NamedTuple{λ::Convex.AbstractExpr, w::Convex.AbstractExpr, Z::Convex.AbstractExpr}

```

Schur complement form of weighted θ from theorem 14 of arxiv:2101.00162.

Returns λ, w, and Z variables (for Convex.jl) in a named tuple.

See also: [`dsw_schur2`](@ref).
