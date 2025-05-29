```
counts(a::ClusteringResult, b::ClusteringResult) -> Matrix{Int}
counts(a::ClusteringResult, b::AbstractVector{<:Integer}) -> Matrix{Int}
counts(a::AbstractVector{<:Integer}, b::ClusteringResult) -> Matrix{Int}
```

同じデータポイントの2つのクラスタリングの*クロス集計*（別名*コンティンジェンシー行列*）を計算します。

返されるのは、$n_a × n_b$ 行列 `C` であり、$n_a$ と $n_b$ はそれぞれ `a` と `b` のクラスタの数であり、`C[i, j]` は `a` の i 番目のクラスタと `b` の j 番目のクラスタの交差のサイズです。

クラスタリングは、[`ClusteringResult`](@ref) インスタンスまたはデータポイントの割り当てのベクトルとして指定できます。

## 参照

[`confusion(a::ClusteringResult, a::ClusteringResult)`](@ref confusion) は 2×2 *混同行列* のためのものです。
