```
localmean!(dst, A, B=3; null=zero(eltype(dst)), order=FORWARD_FILTER) -> dst
```

は、`A` の局所平均を `B` で定義された近傍で計算し、`dst` を上書きして返します。

キーワード `null` は、近傍内の重みの合計がゼロの場合の結果の値を指定するために使用できます。

キーワード `order` はフィルタの方向を指定し、デフォルトでは `FORWARD_FILTER` です。

関連情報として [`localmean`](@ref) と [`localfilter!`](@ref) を参照してください。
