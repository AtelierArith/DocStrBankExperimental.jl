```
get_gradient(M::AbstractManifold, emo::EmbeddedManifoldObjective, p)
get_gradient!(M::AbstractManifold, X, emo::EmbeddedManifoldObjective, p)
```

Evaluate the gradient function of an objective defined in the embedding, that is embed `p` before calling the gradient function stored in the [`EmbeddedManifoldObjective`](@ref).

The returned gradient is then converted to a Riemannian gradient calling [`riemannian_gradient`](https://juliamanifolds.github.io/ManifoldDiff.jl/stable/library.html#ManifoldDiff.riemannian_gradient-Tuple{AbstractManifold,%20Any,%20Any}).
