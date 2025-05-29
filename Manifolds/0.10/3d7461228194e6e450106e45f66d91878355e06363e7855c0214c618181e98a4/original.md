```
injectivity_radius(M::AbstractSphere[, p])
```

Return the injectivity radius for the [`AbstractSphere`](@ref) `M`, which is globally $π$.

```
injectivity_radius(M::Sphere, x, ::ProjectionRetraction)
```

Return the injectivity radius for the [`ProjectionRetraction`](@extref `ManifoldsBase.ProjectionRetraction`) on the [`AbstractSphere`](@ref), which is globally $\frac{π}{2}$.
