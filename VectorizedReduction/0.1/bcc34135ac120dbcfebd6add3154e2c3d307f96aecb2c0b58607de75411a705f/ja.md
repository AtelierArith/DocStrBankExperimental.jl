```
vsoftmax(A::AbstractArray, dims)
```

ソフトマックス関数を計算します。`dims` で指定された `A` の各スライスを単一のベクトルとして扱います。`dims` は `::Int`、`::NTuple{M, Int} where {M}` または `::Colon` であることができます。オーバーフロー/アンダーフローを回避しますが、`+Inf` と `NaN` は処理されません。
