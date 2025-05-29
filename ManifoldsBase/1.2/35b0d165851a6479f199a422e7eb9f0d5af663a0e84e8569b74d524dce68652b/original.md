```
sectional_curvature(M::ProductManifold, p, X, Y)
```

Compute the sectional curvature of a manifold $\mathcal M$ at a point $p \in \mathcal M$ on two linearly independent tangent vectors at $p$. It may be 0 for a product of non-flat manifolds if projections of `X` and `Y` on subspaces corresponding to component manifolds are not linearly independent.
