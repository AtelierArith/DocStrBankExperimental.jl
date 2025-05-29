```
get_hessian(M::AbstractManifold, emo::EmbeddedManifoldObjective, p, X)
get_hessian!(M::AbstractManifold, Y, emo::EmbeddedManifoldObjective, p, X)
```

Evaluate the Hessian of an objective defined in the embedding, that is embed `p` and `X` before calling the Hessian function stored in the [`EmbeddedManifoldObjective`](@ref).

The returned Hessian is then converted to a Riemannian Hessian calling  [`riemannian_Hessian`](https://juliamanifolds.github.io/ManifoldDiff.jl/stable/library/#ManifoldDiff.riemannian_Hessian-Tuple{AbstractManifold,%20Any,%20Any,%20Any,%20Any}).
