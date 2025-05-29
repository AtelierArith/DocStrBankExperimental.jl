```
pairwise!(metric::PreMetric, r::AbstractMatrix,
          a::AbstractMatrix, b::AbstractMatrix=a; dims)
```

`a` と `b` の各行 (もし `dims=1` の場合) または列 (もし `dims=2` の場合) の間の距離を距離 `metric` に従って計算し、その結果を `r` に格納します。単一の行列 `a` が提供された場合、その行または列の間の距離を計算します。

`dims=1` の場合、`a` と `b` は同じ列数を持たなければならず、`dims=2` の場合は同じ行数を持たなければなりません。`r` は `size(a, dims) × size(b, dims)` のサイズを持つ行列でなければなりません。
