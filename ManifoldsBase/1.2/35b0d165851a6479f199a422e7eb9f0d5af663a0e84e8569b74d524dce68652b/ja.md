```
sectional_curvature(M::ProductManifold, p, X, Y)
```

多様体 $\mathcal M$ の点 $p \in \mathcal M$ における、2つの線形独立な接ベクトル $p$ に対する断面曲率を計算します。成分多様体に対応する部分空間における `X` と `Y` の射影が線形独立でない場合、非平坦多様体の積に対しては 0 になることがあります。
