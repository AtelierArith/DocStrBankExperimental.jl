```
knn_dists(D, k::Int, temp_excl::Int = 0)
```

は距離行列 `D` の k 最近傍を返します。主対角線の `D` からの `temp_excl`（デフォルト: `temp_excl = 0`）距離を最近傍として除外します。

# 例

```
julia> dc = randn(20, 4,3)
julia> D = dist_matrix(dc, space = 2)
julia> knn_dists_out = knn_dists(D, 3, 1)
julia> knn_dists_out[5] # 距離
julia> knn_dists_out[4] # インデックス
```
