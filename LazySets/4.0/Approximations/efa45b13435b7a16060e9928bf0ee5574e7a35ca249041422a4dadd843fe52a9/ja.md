```
overapproximate(QM::QuadraticMap{N, <:AbstractZonotope},
                ::Type{<:Zonotope}) where {N}
```

ゾノトープ集合の二次写像をゾノトープで過大評価します。

### 入力

  * `QM`       – ゾノトープ集合の二次写像
  * `Zonotope` – 目標集合の型

### 出力

ゾノトープ集合の二次写像を過大評価するゾノトープ。

### 注意事項

数学的には、行列 $Q$ を持つゾノトープの二次写像は次のように定義されます：

$$
    Z_Q = \right\{ λ \mid λ_i = x^T Q\^{(i)} x,~i = 1, …, n,~x ∈ Z \left\}
$$

### アルゴリズム

このメソッドは [AlthoffK12; Lemma 1](@citet) を実装しています。
