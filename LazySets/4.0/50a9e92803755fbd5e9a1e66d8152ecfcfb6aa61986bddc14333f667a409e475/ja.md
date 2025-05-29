# 拡張ヘルプ

```
minkowski_difference(Z1::AbstractZonotope, Z2::AbstractZonotope)
```

### 出力

`HPolytope`。

### アルゴリズム

一次元集合の場合、このメソッドは区間に対する単純なアルゴリズムを実装しています。二次元集合の場合、このメソッドは[Althoff15; Proposition 6](@citet)を実装しています。高次元集合の場合、このメソッドは[Althoff15; Theorem 3](@citet)を実装しています。
