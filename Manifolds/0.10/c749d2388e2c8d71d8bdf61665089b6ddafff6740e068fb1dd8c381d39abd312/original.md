```
rand(::MetricManifold{ℝ,<:ProbabilitySimplex,<:EuclideanMetric}; vector_at=nothing, σ::Real=1.0)
```

When `vector_at` is `nothing`, return a random (uniform) point `x` on the [`ProbabilitySimplex`](@ref) with the Euclidean metric manifold `M` by normalizing independent exponential draws to unit sum, see [Devroye:1986](@cite), Theorems 2.1 and 2.2 on p. 207 and 208, respectively. When `vector_at` is not `nothing`, return a (Gaussian) random vector from the tangent space $T_{p}\mathrm{\Delta}^n$by shifting a multivariate Gaussian with standard deviation `σ` to have a zero component sum.
