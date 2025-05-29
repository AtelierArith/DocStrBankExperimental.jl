```
std_error(B::ErrorPropagator, gradient[, lvl])
```

エラープロパゲーターの引数に作用する関数 `f` の一次標準誤差推定値を返します。`gradient` は `f` の勾配（関数）またはベクトル `∇f(means(B))` のいずれかです。`f` の推定平均値を得るには、`mean(B, f)` を使用できます。
