```
init_knn_dists(T::Int, k::Int)
init_knn_dists(datacube::AbstractArray, k::Int)
```

事前に割り当てられた `knn_dists_out` オブジェクトを初期化します。`k` は最近傍の数、`T` は時間ステップの数（すなわち最初の次元のサイズ）または多次元の `datacube` です。
