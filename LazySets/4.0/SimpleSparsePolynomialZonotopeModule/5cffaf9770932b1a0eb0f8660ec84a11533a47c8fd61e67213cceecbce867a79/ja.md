```
SimpleSparsePolynomialZonotope{N, VN<:AbstractVector{N},
                               MN<:AbstractMatrix{N},
                               ME<:AbstractMatrix{Int}}
    <: AbstractSparsePolynomialZonotope{N}
```

独立生成子と従属生成子の区別がないという意味で*単純*な疎多項式ゾノトープを表す型です。

単純な疎多項式ゾノトープ $\mathcal{PZ} ⊂ ℝ^n$ は次の集合で表されます。

$$
\mathcal{PZ} = \left\{x ∈ ℝ^n : x = c + ∑_{i=1}^h \left(∏_{k=1}^p α_k^{E_{k, i}} \right) g_i,~~ α_k ∈ [-1, 1]~~ ∀ i = 1,…,p \right\},
$$

ここで、$c ∈ ℝ^n$ はオフセットベクトル（または中心）、$G ∈ ℝ^{n × h}$ は列 $g_i$ を持つ生成子行列（各 $g_i$ は*生成子*と呼ばれます）、$E ∈ \mathbb{N}^{p×h}_{≥0}$ は行列要素 $E_{k, i}$ を持つ指数行列です。

### フィールド

  * `c` – オフセットベクトル
  * `G` – 生成子行列
  * `E` – 指数行列

### 注記

疎多項式ゾノトープは [KochdumperA21](@citet) で導入されました。*単純*なバリアントは [Kochdumper21b] で定義されました。
