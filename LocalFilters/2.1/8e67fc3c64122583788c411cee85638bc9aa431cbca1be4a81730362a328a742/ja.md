```
localextrema(A, B=3; order=FORWARD_FILTER) -> Amin, Amax
```

は、`A`の侵食と膨張を、`B`で定義された構造要素によって1回のパスで実行する結果を返します。このメソッドを呼び出すことは、通常、[`erode`](@ref)および[`dilate`](@ref)を呼び出すよりもほぼ2倍速いです。

キーワード`order`はフィルタの方向を指定し、デフォルトでは`FORWARD_FILTER`です。

メソッドのインプレースバージョンについては[`localextrema!`](@ref)を、これらの操作の説明については[`erode`](@ref)または[`dilate`](@ref)を参照してください。
