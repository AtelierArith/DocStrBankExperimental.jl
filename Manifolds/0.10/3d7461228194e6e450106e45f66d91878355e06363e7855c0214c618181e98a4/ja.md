```
injectivity_radius(M::AbstractSphere[, p])
```

[`AbstractSphere`](@ref) `M` の射影半径を返します。これは全体で $π$ です。

```
injectivity_radius(M::Sphere, x, ::ProjectionRetraction)
```

[`AbstractSphere`](@ref) 上の [`ProjectionRetraction`](@extref `ManifoldsBase.ProjectionRetraction`) の射影半径を返します。これは全体で $\frac{π}{2}$ です。
