```
pairwise!(R::AbstractMatrix, dist::Union{StringSemiMetric, StringMetric}, xs::AbstractVector, ys::AbstractVector = xs; preprocess = true)
```

`xs` と `ys` のすべての要素のペア間の距離を `Union{StringSemiMetric, StringMetric}` `dist` に従って計算し、結果を `R` に書き込みます。 `R[i, j]` は `xs[i]` と `ys[j]` の間の距離に対応します。

前処理を使用しない場合は、`preprocess` を false に設定してください。
