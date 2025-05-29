```
quadratic_map(Q::Vector{<:AbstractMatrix}, S::SimpleSparsePolynomialZonotope)
```

単純スパース多項式ゾノトープの二次写像を返します。

### 入力

  * `Q` – 正方行列のベクトル
  * `S` – 単純スパース多項式ゾノトープ

### 出力

`P` の二次写像を単純スパース多項式ゾノトープとして表現します。

### アルゴリズム

このメソッドは [KochdumperA21; Proposition 12](@citet) を実装しています。さらに [Kochdumper21a; Proposition 3.1.30](@citet) も参照してください。
