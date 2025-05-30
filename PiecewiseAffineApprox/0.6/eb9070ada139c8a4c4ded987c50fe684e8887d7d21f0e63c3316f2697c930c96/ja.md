```
approx(f::Function, bbox::Vector{<:Tuple}, c::Curvature, a::Algorithm;  kwargs...)
```

バウンディングボックス `bbox` に対して均一サンプリングを使用して関数を近似します。

追加のキーワード引数:

  * `nsample`: 各次元で使用されるポイントの数 (デフォルト = 10)
