```
var(ep::ErrorPropagator, gradient[, lvl])
```

エラー伝播子の引数に作用する関数 `f` の一次分散推定値を返します。`gradient` は `f` の勾配（関数）またはベクトル `∇f(means(ep))` のいずれかです。`f` の推定平均値を得るには、`mean(ep, f)` を使用できます。
