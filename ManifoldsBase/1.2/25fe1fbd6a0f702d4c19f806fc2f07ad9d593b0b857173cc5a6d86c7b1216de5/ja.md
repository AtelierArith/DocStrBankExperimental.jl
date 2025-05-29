```
sectional_curvature_min(M::AbstractManifold)
```

多様体 `M` の切断曲率の下限。式は次のようになります。

$$
\omega = \operatorname{inf}_{p\in\mathcal M, X\in T_p\mathcal M, Y\in T_p\mathcal M, ⟨X, Y⟩ ≠ 0} \kappa_p(X, Y)
$$
