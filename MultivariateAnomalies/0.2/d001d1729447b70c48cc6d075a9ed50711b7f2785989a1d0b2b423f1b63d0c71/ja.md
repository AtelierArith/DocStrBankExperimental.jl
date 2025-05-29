```
knn_dists!(knn_dists_out, D, temp_excl::Int = 0)
```

は距離行列 `D` の k-最近傍を返します。`knn_dists()` と似ていますが、`init_knn_dists()` で初期化された事前割り当ての入力オブジェクト `knn_dists_out` を使用します。最近傍の数 `k` は必要ありません。なぜなら、それはすでに `knn_dists_out` オブジェクトによって決定されているからです。

# 例

```
julia> dc = randn(20, 4,3)
julia> D = dist_matrix(dc, space = 2)
julia> knn_dists_out = init_knn_dists(dc, 3)
julia> knn_dists!(knn_dists_out, D)
julia> knn_dists_out[5] # 距離
julia> knn_dists_out[4] # インデックス
```
