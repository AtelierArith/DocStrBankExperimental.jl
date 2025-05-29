```
overapproximate(QM::QuadraticMap{N, <:SparsePolynomialZonotope},
                ::Type{<:SparsePolynomialZonotope}) where {N}
```

スパース多項式ゾノトープの二次写像をスパース多項式ゾノトープで上近似します。

### 入力

  * `QM`                       – スパース多項式ゾノトープの二次写像
  * `SparsePolynomialZonotope` – 目標タイプ

### 出力

スパース多項式ゾノトープの二次写像を上近似するスパース多項式ゾノトープ。

### アルゴリズム

このメソッドは[KochdumperA21; Proposition 13](@citet)を実装しています。
