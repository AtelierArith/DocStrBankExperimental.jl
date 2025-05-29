```
dist_matrix(data::AbstractArray{tp, N}; dist::String = "Euclidean", space::Int = 0, lat::Int = 0, lon::Int = 0, Q = 0) where {tp, N}
dist_matrix(data::AbstractArray{tp, N}, training_data; dist::String = "Euclidean", space::Int = 0, lat::Int = 0, lon::Int = 0, Q = 0) where {tp, N}
```

`data`の距離行列またはデータとトレーニングデータ間の距離行列を計算します。すなわち、データの最初の次元に沿ったペアワイズ距離を計算し、最後の次元を変数として使用します。`dist`は距離メトリックであり、現在は`Euclidean`（デフォルト）、`SqEuclidean`、`Chebyshev`、`Cityblock`、`JSDivergence`、`Mahalanobis`、および`SqMahalanobis`がサポートされています。後者の2つは、入力引数として共分散行列`Q`が必要です。

# 例

```
julia> dc = randn(10, 4,3)
julia> D = dist_matrix(dc, space = 2)
```
