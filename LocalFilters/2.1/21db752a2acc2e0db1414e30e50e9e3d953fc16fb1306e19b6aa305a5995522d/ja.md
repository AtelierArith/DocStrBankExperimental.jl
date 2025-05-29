```
localextrema!(Amin, Amax, A, B=3; order=FORWARD_FILTER) -> Amin, Amax
```

は、配列 `A` の構造要素として定義された `B` によって、配列 `A` の侵食と膨張をそれぞれ `Amin` と `Amax` に上書きします。

キーワード `order` はフィルタの方向を指定し、デフォルトでは `FORWARD_FILTER` です。

詳細については、[`localextrema`](@ref) の非破壊バージョンを参照してください。
