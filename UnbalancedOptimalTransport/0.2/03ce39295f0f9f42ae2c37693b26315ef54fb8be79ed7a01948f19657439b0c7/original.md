```
sinkhorn_divergence!(
    D::AbstractDivergence,
    C,
    a::DiscreteMeasure,
    b::DiscreteMeasure,
    ϵ = 1e-1;
    kwargs...,
) -> Number
```

Computes the unbalanced sinkhorn divergence between `a` and `b` as defined in Def. 6 of [[SFVTP19](@ref)], using [`unbalanced_sinkhorn!`](@ref); see that function for the meaning of the parameters and the keyword arguments. Sets the optimal `dual_potential`'s of `a` and `b`.
