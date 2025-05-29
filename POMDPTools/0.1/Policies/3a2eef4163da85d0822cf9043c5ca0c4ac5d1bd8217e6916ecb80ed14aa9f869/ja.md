```
CategoricalTabularPolicy
```

は、`ValuePolicy`によって与えられた重みを持つカテゴリカル分布からアクションをサンプリングする確率的ポリシーを表します。

コンストラクタ:

`CategoricalTabularPolicy(mdp::Union{POMDP,MDP}; rng=Random.default_rng())`

# フィールド

  * `stochastic::StochasticPolicy`
  * `value::ValuePolicy`
