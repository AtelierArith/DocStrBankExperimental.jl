```
colwise(metric::PreMetric, a::AbstractMatrix, b::AbstractMatrix)
colwise(metric::PreMetric, a::AbstractVector, b::AbstractMatrix)
colwise(metric::PreMetric, a::AbstractMatrix, b::AbstractVector)
```

`a` と `b` の対応する列間の距離を、距離 `metric` に従って計算します。`a` または `b` のいずれか一方だけがベクトルである必要があり、その場合、そのベクトルと他の行列のすべての列との距離が計算されます。

`a` と `b` は、どちらもベクトルでない場合、同じ数の列を持っている必要があります。

!!! note
    `a` と `b` の両方がベクトルである場合、`colwise` の一般的なイテレータベースのメソッドが適用されます。

