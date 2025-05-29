```
elbo(flow, logp, xs) 
elbo([rng, ]flow, logp, n_samples)
```

参照分布 `flow.dist` からのサンプル `xs` のバッチに対する ELBO を計算します。

# 引数

  * `rng`: 擬似乱数生成器
  * `flow`: 学習される変分分布。特に `flow = transformed(q₀, T::Bijectors.Bijector)` の形をとり、q₀ は簡単にサンプリングし logpdf を計算できる参照分布です。
  * `logp`: 目標分布の log-pdf（必ずしも正規化されているわけではありません）
  * `xs`: 参照分布 q₀ からのサンプル
  * `n_samples`: 参照分布 q₀ からのサンプル数
