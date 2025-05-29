```
vlogsumexp(A::AbstractArray, dims)
```

`A`の各要素の指数の合計の対数を、次元`dims`に沿って計算します。`dims`は`::Int`、`::NTuple{M, Int} where {M}`、または`::Colon`の形式を取ることができます。オーバーフロー/アンダーフローを回避しますが、`+Inf`および`NaN`は処理されません。
