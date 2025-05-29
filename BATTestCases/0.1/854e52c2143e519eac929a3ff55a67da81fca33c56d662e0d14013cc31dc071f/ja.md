```
struct FunnelDistribution <: Distribution{Multivariate,Continuous}
```

*実験的な機能であり、安定した公開APIの一部ではありません。*

ファネル分布（定義については[カルドウェルら](https://arxiv.org/abs/1808.08051)を参照）。

コンストラクタ:

  * `FunnelDistribution(; a::Real = 1.0, b::Real = 0.5, n::Integer = 3)`

フィールド:

  * `a::Real`: 支配的な正規分布の分散。
  * `b::Real`: 補助的な正規分布の分散。
  * `n::Integer`: 次元の数。
