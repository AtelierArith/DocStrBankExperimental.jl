```
kmeans_clustering(data::Vector{Float64}, k_means::Int, max_iters::Int=100, tol::Float64=1e-6)
```

ベクトルデータに対してK-meansクラスタリングを実行します。

# 引数

  * `data::Vector{Float64}`: 入力データベクトル。
  * `k_means::Int`: クラスタの数。
  * `max_iters::Int=100`: 最大反復回数。
  * `tol::Float64=1e-6`: 収束許容値。

# 戻り値

  * 最終的なセントロイドと各データポイントのクラスタラベルを含むタプル。
