```
sectional_curvature_max(M::AbstractPowerManifold)
```

Upper bound on sectional curvature of [`AbstractPowerManifold`](@ref) `M`. It is the maximum of sectional curvature of the wrapped manifold and 0 in case there are two or more component manifolds, as the sectional curvature corresponding to the plane spanned by vectors `(X_1, 0, ... 0)` and `(0, X_2, 0, ..., 0)` is 0.
