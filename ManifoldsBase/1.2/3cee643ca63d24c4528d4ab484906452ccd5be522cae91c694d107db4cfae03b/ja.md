```
sectional_curvature_max(M::AbstractPowerManifold)
```

[`AbstractPowerManifold`](@ref) `M` の断面曲率の上限。これは、ラップされた多様体の断面曲率の最大値と、コンポーネント多様体が2つ以上ある場合の0の最大値です。ベクトル `(X_1, 0, ... 0)` と `(0, X_2, 0, ..., 0)` によって張られる平面に対応する断面曲率は0です。
