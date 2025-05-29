```
loglikelihood(rng, flow::Bijectors.TransformedDistribution, xs::AbstractVecOrMat)
```

ターゲット分布 p からのサンプル xs のバッチに対して、変分分布フローの対数尤度を計算します。

# 引数

  * `rng`: 乱数生成器（空の引数、他の変分目的と同じシグネチャを確保するためにのみ必要）
  * `flow`: 学習される変分分布。特に「flow = transformed(q₀, T::Bijectors.Bijector)」、q₀ は簡単にサンプリングし、logpdf を計算できる参照分布です。
  * `xs`: ターゲット分布 p からのサンプル。
