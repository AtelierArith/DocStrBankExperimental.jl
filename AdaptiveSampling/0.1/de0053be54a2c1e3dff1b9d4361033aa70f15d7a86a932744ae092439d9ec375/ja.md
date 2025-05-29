```
CompositeCost{N, M} <: AbstractCost{N}
```

複数のコスト関数を組み合わせて合成コストを生成するコスト関数です。合成コストは、個々のコストの加重和です：

$$
cost(x, y) = \sum_{k=1}^{M} w_k c_k(x, y)
$$

ここで `c_k` は `k` 番目の個別コスト関数であり、`w_k` は `k` 番目のコスト関数の重みです。重みは合計が1になるように正規化されています。

重みが `Inf` に設定されている場合、合成コストは個別コストの最大値になります。それ以外の場合、合成コストは個別コストの加重平均になります。

# 型パラメータ

  * `N`: 合成コスト関数が考慮する最大隣接数。
  * `M`: 合成コストに組み合わされる個別コスト関数の数。

# フィールド

  * `costs::NTuple{M, AbstractCost}`: 個別コスト関数のタプル。
  * `weights::NTuple{M, Float64}`: 個別コスト関数の重みのタプル。

# コンストラクタ

  * `CompositeCost(costs::NTuple{M, AbstractCost}, weights::NTuple{M, Real}) where {M}`: 指定されたコスト関数と重みを持つ `CompositeCost` を作成します。重みは合計が1になるように正規化されます。
  * `CompositeCost(costs::Vararg{AbstractCost, M}) where {M}`: 指定されたコスト関数とデフォルトの重み `Inf` を持つ `CompositeCost` を作成します。
