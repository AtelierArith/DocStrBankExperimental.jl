```
dbscan_label(tree::AbstractMatrix{<:Real}, radius::Real; min_neighbors::Int64 = 1, min_cluster_size::Int64 = 1)
```

ノイズを伴うアプリケーションの密度ベースの空間クラスタリングから、系統樹のグループに対する予測ラベルを取得します。

# 引数

  * `tree`: B * N のツリーマトリックス（ツリーマトリックスの各列は、二分割形式の B 次元ツリーであり、B < N）。
  * `radius`: 隣接半径。この距離内の点は隣接点と見なされます。
  * `min_neighbors`: 点をクラスタに割り当てるために必要な最小隣接点数。
  * `min_cluster_size`: クラスタ内の最小点数。

# 出力

各ツリーに対する予測ラベルを含む長さ N の `Vector` オブジェクト（それが属するクラスタ）。0はツリーがノイズであることを意味します。
