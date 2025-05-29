```julia
dsw_schur2(
    g::NoncommutativeGraphs.S0Graph
) -> @NamedTuple{λ::Convex.AbstractExpr, w::Convex.AbstractExpr, Z::Convex.AbstractExpr}

```

重み付きθのシュール補完形式は、arxiv:2101.00162の定理14からのもので、S₀ ≠ ℂIの場合に最適化されており、wはS₁（S₀の共役）に制約されています。

λ、w、およびZ変数（Convex.jl用）を名前付きタプルで返します。

関連情報: [`dsw_schur2`](@ref).
