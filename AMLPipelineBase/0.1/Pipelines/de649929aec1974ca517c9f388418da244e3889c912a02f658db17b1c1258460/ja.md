```
ComboPipeline(machs::Vector{T}) where {T<:Machine}
```

フィーチャー結合パイプラインで、各要素の `fit_transform` を反復的に呼び出し、その出力を1つのデータフレームに連結します。

`fit!` と `transform!` を実装しています。
