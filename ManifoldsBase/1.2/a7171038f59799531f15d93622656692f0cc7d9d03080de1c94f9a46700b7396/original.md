```
sectional_curvature(M::AbstractPowerManifold, p, X, Y)
```

Compute the sectional curvature of a power manifold manifold $\mathcal M$ at a point $p \in \mathcal M$ on two linearly independent tangent vectors at $p$. It may be 0 for  if projections of `X` and `Y` on subspaces corresponding to component manifolds are not linearly independent.
