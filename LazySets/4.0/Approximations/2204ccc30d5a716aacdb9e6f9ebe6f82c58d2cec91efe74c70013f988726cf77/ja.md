```
overapproximate(P::DensePolynomialZonotope, ::Type{<:Zonotope})
```

多項式ゾノトープをゾノトープで上近似します。

### 入力

  * `P`        – 多項式ゾノトープ
  * `Zonotope` – 目標集合の型

### 出力

ゾノトープ。

### アルゴリズム

このメソッドは [Althoff13; Proposition 1](@citet) を実装しています。
