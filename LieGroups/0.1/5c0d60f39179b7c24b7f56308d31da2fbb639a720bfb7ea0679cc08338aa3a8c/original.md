```
exp(G::AbstractLieGroup, g, X)
exp!(G::AbstractLieGroup, h, g, X)
```

Compute the Lie group exponential map for $g∈\mathcal G$ and $X∈\mathfrak g$, where $\mathfrak g$ denotes the [`LieAlgebra`](@ref) of $\mathcal G$. It is given by

$$
\exp_g X = g∘\exp_{\mathcal G}(X)
$$

where `X` can be scaled by `t`, the computation can be performed in-place of `h`, and $\exp_{\mathcal G}$ denotes the  [Lie group exponential function](@ref exp(::AbstractLieGroup, ::Identity, :Any)).

If `g` is the [`Identity`](@ref) the [Lie group exponential function](@ref exp(::AbstractLieGroup, ::Identity, :Any)) $\exp_{\mathcal G}$ is computed directly. Implementing the Lie group exponential function introduces a default implementation with the formula above.

!!! note
    The Lie group exponential map is usually different from the exponential map with respect to the metric of the underlying Riemannian manifold $\mathcal M$. To access the (Riemannian) exponential map, use `exp(`[`base_manifold`](@ref)`(G), g, X)`.

