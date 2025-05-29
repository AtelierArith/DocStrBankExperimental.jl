```
sectional_curvature_min(M::AbstractManifold)
```

Lower bound on sectional curvature of manifold `M`. The formula reads

$$
\omega = \operatorname{inf}_{p\in\mathcal M, X\in T_p\mathcal M, Y\in T_p\mathcal M, ⟨X, Y⟩ ≠ 0} \kappa_p(X, Y)
$$
