```
varN(B::ErrorPropagator, gradient[, lvl])

関数 `f` がエラープロパゲータの引数に作用する際の一次の分散/N 推定値を提供します。`gradient` は `f` の勾配（関数）またはベクトル `∇f(means(B))` です。`f` の推定平均値を得るには、`mean(B, f)` を使用できます。
```
