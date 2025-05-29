```
sectional_curvature_min(M::ProductManifold)
```

Lower bound on sectional curvature of [`ProductManifold`](@ref) `M`. It is the minimum of sectional curvatures of component manifolds and 0 in case there are two or more component manifolds, as the sectional curvature corresponding to the plane spanned by vectors `(X_1, 0)` and `(0, X_2)` is 0.
