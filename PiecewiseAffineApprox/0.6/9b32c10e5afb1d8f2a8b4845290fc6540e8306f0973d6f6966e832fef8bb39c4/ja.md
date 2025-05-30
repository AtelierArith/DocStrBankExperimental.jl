```
approx(input::FunctionEvaluations, c::Convex, a::Cluster)
```

一般的な次元に対して機能するヒューリスティックを使用して近似します。

追加のキーワード引数:

  * `trials`: リスタートの回数 (デフォルト = 20)
  * `itlim`: 各試行での最大精緻化反復回数 (デフォルト = 50),
