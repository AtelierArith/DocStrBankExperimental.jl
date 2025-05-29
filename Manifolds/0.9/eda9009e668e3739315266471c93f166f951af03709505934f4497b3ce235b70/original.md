```
exp(::TraitList{IsConnectionManifold}, M::AbstractDecoratorManifold, p, X)
```

Compute the exponential map on a manifold that [`IsConnectionManifold`](@ref) `M` equipped with corresponding affine connection.

If `M` is a [`MetricManifold`](@ref) with a [`IsDefaultMetric`](@ref) trait, this method falls back to `exp(M, p, X)`.

Otherwise it numerically integrates the underlying ODE, see [`solve_exp_ode`](@ref). Currently, the numerical integration is only accurate when using a single coordinate chart that covers the entire manifold. This excludes coordinates in an embedded space.
