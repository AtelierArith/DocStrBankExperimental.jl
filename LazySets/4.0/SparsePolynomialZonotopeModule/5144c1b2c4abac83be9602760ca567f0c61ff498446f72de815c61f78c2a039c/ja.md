```
SparsePolynomialZonotope{N, VN<:AbstractVector{N}, MN<:AbstractMatrix{N},
                         MNI<:AbstractMatrix{N},
                         ME<:AbstractMatrix{Int},
                         VI<:AbstractVector{Int}}
    <: AbstractSparsePolynomialZonotope{N}
```

スパース多項式ゾノトープを表す型。

スパース多項式ゾノトープ $\mathcal{PZ} ⊂ ℝ^n$ は次の集合で表されます。

$$
\mathcal{PZ} = \left\{x ∈ ℝ^n : x = c + ∑ᵢ₌₁ʰ\left(∏ₖ₌₁ᵖ α_k^{E_{k, i}} \right)Gᵢ+∑ⱼ₌₁^qβⱼGIⱼ,~~ α_k, βⱼ ∈ [-1, 1],~~ ∀ k = 1,…,p, j=1,…,q \right\},
$$

ここで、$c ∈ ℝ^n$ はオフセットベクトル（または中心）、$Gᵢ ∈ ℝ^{n}$ は従属生成器、$GIⱼ ∈ ℝ^{n}$ は独立生成器、$E ∈ \mathbb{N}^{p×h}_{≥0}$ は行列要素 $E_{k, i}$ を持つ指数行列です。

実装では、$Gᵢ ∈ ℝ^n$ は従属生成器行列 $G ∈ ℝ^{n × h}$ の列として配置され、同様に $GIⱼ ∈ ℝ^{n}$ は独立生成器行列 $GI ∈ ℝ^{n×q}$ の列として配置されます。

短縮表記 $\mathcal{PZ} = ⟨ c, G, GI, E, idx ⟩$ がよく使用され、ここで $idx ∈ \mathbb{N}^p$ は各従属因子 $αₖ$ の一意の識別子を格納する重複しない自然数のリストです。

### フィールド

  * `c`   – オフセットベクトル
  * `G`   – 従属生成器行列
  * `GI`  – 独立生成器行列
  * `E`   – 指数行列
  * `idx` – 従属パラメータの正の整数の識別子ベクトル

### ノート

スパース多項式ゾノトープは [KochdumperA21](@citet) で導入されました。
