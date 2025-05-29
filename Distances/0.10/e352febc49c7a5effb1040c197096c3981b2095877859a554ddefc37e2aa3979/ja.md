```
pairwise(metric::PreMetric, a::AbstractMatrix, b::AbstractMatrix=a; dims)
```

距離 `metric` に従って、`a` と `b` の各行（`dims=1` の場合）または列（`dims=2` の場合）間の距離を計算します。単一の行列 `a` が提供された場合、その行または列間の距離を計算します。

`a` と `b` は、`dims=1` の場合は同じ数の列を、`dims=2` の場合は同じ数の行を持っている必要があります。
