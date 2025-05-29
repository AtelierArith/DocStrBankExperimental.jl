```
std_error(ep::ErrorPropagator, gradient[, lvl])
```

エラープロパゲーターの引数に作用する関数 `f` の一次標準誤差推定値を提供します。`gradient` は `f` の勾配（関数）またはベクトル `∇f(means(ep))` のいずれかです。`f` の推定平均値を取得するには、`mean(ep, f)` を使用できます。
