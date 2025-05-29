```julia
dsw_schur(
    g::NoncommutativeGraphs.S0Graph
) -> @NamedTuple{λ::Convex.AbstractExpr, w::Convex.AbstractExpr, Z::Convex.AbstractExpr}

```

arxiv:2101.00162の定理14からの重み付きθのシュール補完形式。

λ、w、およびZ変数（Convex.jl用）を名前付きタプルで返します。

関連情報: [`dsw_schur2`](@ref).
