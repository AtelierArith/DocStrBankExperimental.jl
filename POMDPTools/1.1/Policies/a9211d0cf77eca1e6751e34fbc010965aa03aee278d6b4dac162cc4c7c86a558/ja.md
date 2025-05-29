StochasticPolicy{D, RNG <: AbstractRNG}

確率的ポリシーを表します。アクションは任意の分布からサンプリングされます。

コンストラクタ:

```
`StochasticPolicy(distribution; rng=Random.default_rng())`
```

# フィールド

  * `distribution::D`
  * `rng::RNG` ランダム数生成器
