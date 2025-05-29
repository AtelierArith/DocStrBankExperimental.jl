```
vtlogsoftmax(A::AbstractArray, dims)
```

各スライス `A` を `dims` で指定されたように単一のベクトルとして扱い、ソフトマックス関数の対数を計算します。`dims` は `::Int`、`::NTuple{M, Int} where {M}` または `::Colon` で指定できます。スレッド対応。オーバーフロー/アンダーフローを回避しますが、`+Inf` および `NaN` は処理されません。
