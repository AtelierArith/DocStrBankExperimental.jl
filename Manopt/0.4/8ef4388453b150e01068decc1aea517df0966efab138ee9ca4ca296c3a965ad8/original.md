```
X = get_grad_inequality_constraint(M::AbstractManifold, emo::EmbeddedManifoldObjective, p, j)
get_grad_inequality_constraint!(M::AbstractManifold, X, emo::EmbeddedManifoldObjective, p, j)
```

Evaluate the gradient of the `j`th inequality constraint $\operatorname{grad} g_j(p)$ defined in the embedding, that is embed `p` before calling the gradient function stored in the [`EmbeddedManifoldObjective`](@ref).

The returned gradient is then converted to a Riemannian gradient calling [`riemannian_gradient`](https://juliamanifolds.github.io/ManifoldDiff.jl/stable/library.html#ManifoldDiff.riemannian_gradient-Tuple{AbstractManifold,%20Any,%20Any}).
