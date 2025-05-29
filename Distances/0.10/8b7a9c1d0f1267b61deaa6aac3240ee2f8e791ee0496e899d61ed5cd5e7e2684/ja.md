```
colwise!(metric::PreMetric, r::AbstractArray,
         a::AbstractMatrix, b::AbstractMatrix)
colwise!(metric::PreMetric, r::AbstractArray,
         a::AbstractVector, b::AbstractMatrix)
colwise!(metric::PreMetric, r::AbstractArray,
         a::AbstractMatrix, b::AbstractVector)
```

`a` と `b` の各対応する列間の距離を距離 `metric` に従って計算し、その結果を `r` に格納します。`a` または `b` のいずれか一方だけがベクトルである必要があり、その場合はそのベクトルと他の行列のすべての列との距離が計算されます。

`a` と `b` は、どちらもベクトルでない場合、同じ数の列を持っている必要があります。`r` は `maximum(size(a, 2), size(b, 2))` の長さの配列でなければなりません。

!!! note
    `a` と `b` の両方がベクトルである場合、`colwise` の一般的なイテレータベースのメソッドが適用されます。

