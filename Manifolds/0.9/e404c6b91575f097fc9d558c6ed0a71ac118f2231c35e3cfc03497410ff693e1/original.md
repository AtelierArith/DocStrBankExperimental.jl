```
log(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},<:StiefelSubmersionMetric}, p, q; kwargs...)
```

Compute the logarithmic map on the [`Stiefel(n,k)`](@ref) manifold with respect to the [`StiefelSubmersionMetric`](@ref).

The logarithmic map is computed using [`ShootingInverseRetraction`](@extref `ManifoldsBase.ShootingInverseRetraction`). For $k ≤ \lfloor\frac{n}{2}\rfloor$, this is sped up using the $k$-shooting method of [ZimmermannHueper:2022](@cite). Keyword arguments are forwarded to `ShootingInverseRetraction`; see that documentation for details. Their defaults are:

  * `num_transport_points=4`
  * `tolerance=sqrt(eps())`
  * `max_iterations=1_000`
