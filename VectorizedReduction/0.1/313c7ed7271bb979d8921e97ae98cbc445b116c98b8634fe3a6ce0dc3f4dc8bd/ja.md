```
vlogsoftmax(A::AbstractArray, dims)
```

各スライスをベクトルとして扱い、`dims` で指定された `A` のソフトマックス関数の対数を計算します。`dims` は `::Int`、`::NTuple{M, Int} where {M}` または `::Colon` で指定できます。オーバーフロー/アンダーフローを回避しますが、`+Inf` と `NaN` は処理されません。
