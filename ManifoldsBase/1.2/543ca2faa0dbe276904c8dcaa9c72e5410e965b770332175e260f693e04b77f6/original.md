```
sectional_curvature_max(M::AbstractManifold)
```

Upper bound on sectional curvature of manifold `M`. The formula reads

$$
\omega = \operatorname{sup}_{p\in\mathcal M, X\in T_p\mathcal M, Y\in T_p\mathcal M, ⟨X, Y⟩ ≠ 0} \kappa_p(X, Y)
$$
