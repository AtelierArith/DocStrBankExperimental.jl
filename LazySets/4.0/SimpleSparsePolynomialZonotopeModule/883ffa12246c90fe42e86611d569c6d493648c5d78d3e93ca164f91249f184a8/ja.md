```
quadratic_map(Q::Vector{<:AbstractMatrix}, S1::SimpleSparsePolynomialZonotope,
              S2::SimpleSparsePolynomialZonotope)
```

2つの単純スパース多項式ゾノトープの二次写像を返します。二次写像は次の集合です。

$$
    \{x \mid xᵢ = s₁ᵀQᵢs₂, s₁ ∈ S₁, s₂ ∈ S₂, Qᵢ ∈ Q\}.
$$

### 入力

  * `Q`  – 正方行列のベクトル
  * `S1` – 単純スパース多項式ゾノトープ
  * `S2` – 単純スパース多項式ゾノトープ

### 出力

与えられた単純スパース多項式ゾノトープの二次写像を、単純スパース多項式ゾノトープとして表現します。

### アルゴリズム

このメソッドは[Kochdumper21a; Proposition 3.1.30](@citet)を実装しています。
