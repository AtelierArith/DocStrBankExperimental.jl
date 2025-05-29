# 拡張ヘルプ

```
linear_map(M::AbstractMatrix, E::Ellipsoid)
```

### アルゴリズム

楕円体 $⟨c, Q⟩$ と行列 $M$ が与えられたとき、線形写像は楕円体 $⟨M c, M Q Mᵀ⟩$ を生成します。
