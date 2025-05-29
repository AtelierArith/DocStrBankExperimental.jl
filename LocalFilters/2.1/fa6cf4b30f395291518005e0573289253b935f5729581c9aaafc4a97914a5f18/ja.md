```
localmap!(f, dst, A, B=3; null=zero(eltype(dst)), order=FORWARD_FILTER)
```

各エントリの `dst` を、`B` によって定義された近傍から抽出された `A` の値に関数 `f` を適用した結果に設定します。

関数 `f` は、空の値ベクトルで呼び出されることはありません。キーワード `null` は、近傍が空の場合の結果の値を指定するために使用できます。デフォルトでは、`null = zero(T)` で、`T` は結果の要素型です。

キーワード `order` はフィルタの方向を指定し、デフォルトでは `FORWARD_FILTER` です。
