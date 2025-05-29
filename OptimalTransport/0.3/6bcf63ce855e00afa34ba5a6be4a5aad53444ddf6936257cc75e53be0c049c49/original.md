```
sinkhorn_divergence(
    μ,
    ν,
    Cμν,
    Cμ,
    Cν,
    ε,
    alg::SinkhornDivergence=SinkhornDivergence(
        SinkhornGibbs(), SymmetricSinkhornGibbs(), SymmetricSinkhornGibbs()
    );
    kwargs...,
)
```

Compute the Sinkhorn Divergence between finite discrete measures `μ` and `ν` with respect to the precomputed cost matrices `Cμν`, `Cμμ` and `Cνν`, entropic regularization parameter `ε` and algorithm `alg`.

A pre-computed optimal transport `plan` between `μ` and `ν` may be provided.

See also: [`sinkhorn2`](@ref), [`sinkhorn_divergence`](@ref)
