```
dists, inds = sparse_distmat(y::Vector{<:AbstractVector{T}}, k, dist, radius; kwargs...) where T
```

信号 `y` の間で `k` 最近傍を計算し、ペアワイズ距離行列の各行の中で `k` 最小のエントリに対応します。返される値は、計算された距離と隣接インデックスを持つ長さ-k のベクトルのベクトルです。

# 引数:

  * `y`: 信号を含むベクトルのベクトル
  * `k`: 隣接数
  * `dist`: 内部メトリック、例: `SqEuclidean()`
  * `kwargs`: これらは `dtw_cost` に送信されます。
  * `showprogress = true`
