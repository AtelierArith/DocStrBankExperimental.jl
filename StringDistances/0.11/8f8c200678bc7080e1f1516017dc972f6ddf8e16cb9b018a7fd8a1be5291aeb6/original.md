```
pairwise!(R::AbstractMatrix, dist::Union{StringSemiMetric, StringMetric}, xs::AbstractVector, ys::AbstractVector = xs; preprocess = true)
```

Compute distances between all pairs of elements in `xs` and `ys` according to the `Union{StringSemiMetric, StringMetric}` `dist` and write the result in `R`. `R[i, j]` corresponds to the distance between `xs[i]` and `ys[j]`.

Set `preprocess` to false if no preprocessing should be used.
