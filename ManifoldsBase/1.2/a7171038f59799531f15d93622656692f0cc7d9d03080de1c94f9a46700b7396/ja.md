```
sectional_curvature(M::AbstractPowerManifold, p, X, Y)
```

パワーマニホールド $\mathcal M$ の点 $p \in \mathcal M$ における断面曲率を、$p$ における2つの線形独立な接ベクトルに対して計算します。`X` と `Y` の成分マニホールドに対応する部分空間への射影が線形独立でない場合、0になることがあります。
