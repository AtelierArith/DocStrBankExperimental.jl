```
kmeans_clustering(data::Matrix{<:Real}, k_means::Int, max_iters::Int=100, tol::Float64=1e-6)
```

入力データに対してK-meansクラスタリングを実行します。

# 引数

  * `data::Matrix{<:Real}`: 各行がデータポイントである入力データ行列。
  * `k_means::Int`: クラスターの数。
  * `max_iters::Int=100`: 最大反復回数。
  * `tol::Float64=1e-6`: 収束許容誤差。

# 戻り値

  * 最終的なセントロイドと各データポイントのクラスタラベルを含むタプル。
