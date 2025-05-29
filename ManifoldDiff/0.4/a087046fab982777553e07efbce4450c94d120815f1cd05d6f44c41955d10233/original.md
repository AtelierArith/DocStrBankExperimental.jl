```
RiemannianProjectionBackend <: AbstractRiemannianDiffBackend
```

This backend computes the differentiation in the embedding, which is currently limited to the gradient. Let $mathcal M$ denote a manifold embedded in some $R^m$, where $m$ is usually (much) larger than the manifold dimension. Then we require three tools

  * A function $f̃: ℝ^m → ℝ$ such that its restriction to the manifold yields the cost function $f$ of interest.
  * A [`project`](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/projections.html#ManifoldsBase.project-Tuple{AbstractManifold,%20Any,%20Any}) function to project tangent vectors from the embedding (at $T_pℝ^m$) back onto the tangent space $T_p\mathcal M$. This also includes possible changes of the representation of the tangent vector (e.g. in the Lie algebra or in a different data format).
  * A [`change_representer`](https://juliamanifolds.github.io/Manifolds.jl/stable/manifolds/metric.html#Manifolds.change_metric-Tuple{AbstractManifold,%20AbstractMetric,%20Any,%20Any}) for non-isometrically embedded manifolds, i.e. where the tangent space $T_p\mathcal M$ of the manifold does not inherit the inner product from restriction of the inner product from the tangent space $T_pℝ^m$ of the embedding

see also [`riemannian_gradient`](@ref) and [AbsilMahonySepulchre:2008](@cite), Section 3.6.1 for a derivation on submanifolds.
