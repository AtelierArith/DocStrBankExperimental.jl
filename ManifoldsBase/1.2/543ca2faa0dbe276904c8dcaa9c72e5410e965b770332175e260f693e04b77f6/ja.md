```
sectional_curvature_max(M::AbstractManifold)
```

多様体 `M` の切断曲率の上限。式は次のようになります。

$$
\omega = \operatorname{sup}_{p\in\mathcal M, X\in T_p\mathcal M, Y\in T_p\mathcal M, ⟨X, Y⟩ ≠ 0} \kappa_p(X, Y)
$$
