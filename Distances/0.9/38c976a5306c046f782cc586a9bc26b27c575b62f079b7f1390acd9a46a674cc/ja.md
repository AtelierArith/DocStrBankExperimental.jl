```
pairwise!(r::AbstractMatrix, metric::PreMetric,
          a::AbstractMatrix, b::AbstractMatrix=a; dims)
```

行列 `a` と `b` の各行のペア（`dims=1` の場合）または列のペア（`dims=2` の場合）間の距離を距離 `metric` に従って計算し、その結果を `r` に格納します。単一の行列 `a` が提供された場合、その行または列間の距離を計算します。

`a` と `b` は、`dims=1` の場合は同じ数の列を持ち、`dims=2` の場合は同じ数の行を持たなければなりません。`r` は、`size(a, dims) == size(b, dims)` のサイズを持つ正方行列でなければなりません。
