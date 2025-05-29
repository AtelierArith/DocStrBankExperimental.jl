# 拡張ヘルプ

```
ρ(d::AbstractVector, E::Ellipsoid)
```

### アルゴリズム

サポート値は $cᵀ d + ‖Bᵀ d‖₂$ であり、ここで $c$ は中心で、$Q = B Bᵀ$ は `E` の形状行列です。
