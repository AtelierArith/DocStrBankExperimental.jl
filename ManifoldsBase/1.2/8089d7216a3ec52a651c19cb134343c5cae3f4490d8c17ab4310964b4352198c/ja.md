```
sectional_curvature_max(M::ProductManifold)
```

[`ProductManifold`](@ref) `M`の断面曲率の上限。これは、構成多様体の断面曲率の最大値であり、構成多様体が2つ以上ある場合は0です。なぜなら、ベクトル `(X_1, 0)` と `(0, X_2)` によって張られる平面に対応する断面曲率は0だからです。
