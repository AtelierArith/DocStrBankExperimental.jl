# 拡張ヘルプ

```
minkowski_sum(PZ::DensePolynomialZonotope, Z::AbstractZonotope)
```

## 出力

`DensePolynomialZonotope`。

### アルゴリズム

多項式ゾノトープの中心は `PZ` と `Z` の中心の和であり、その生成子は `PZ` と `Z` の生成子の連結です。
