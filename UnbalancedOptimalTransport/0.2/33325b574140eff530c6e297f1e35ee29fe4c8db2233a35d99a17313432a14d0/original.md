```
function optimal_coupling!(
    D::AbstractDivergence,
    C,
    a::DiscreteMeasure,
    b::DiscreteMeasure,
    ϵ = 1e-1;
    dual_potentials_populated::Bool = false,
    kwargs...) -> Matrix
```

Computes the optimal coupling between `a` and `b` using the optimal dual potentials, the regularization parameter `ϵ`, and the cost function `C`.

If `dual_potentials_populated = false`, [`unbalanced_sinkhorn!`](@ref) is called to populate the dual potentials of `a` and `b`, using the divergence `D`. If `dual_potentials_populated = true`, one of [`unbalanced_sinkhorn!`](@ref) or [`OT!`](@ref) or [`sinkhorn_divergence!`](@ref) must be called first to set the optimal dual potentials, with the same choice of `ϵ` and `C`. In this case, `a` and `b` are not mutated.

This function implements Prop. 6 of [[SFVTP19](@ref)].
