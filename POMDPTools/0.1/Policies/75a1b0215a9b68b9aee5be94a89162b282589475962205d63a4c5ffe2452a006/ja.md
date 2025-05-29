```
EpsGreedyPolicy <: ExplorationPolicy
```

は、確率 `eps` でランダムなアクションをサンプリングするか、そうでなければ与えられたポリシーからアクションを返すイプシロン・グリーディポリシーを表します。イプシロンの進化はスケジュールを使用して制御できます。この機能は、強化学習アルゴリズムでこれらのポリシーを使用する際に便利です。

# コンストラクタ:

`EpsGreedyPolicy(problem::Union{MDP, POMDP}, eps::Union{Function, Float64}; rng=Random.default_rng(), schedule=ConstantSchedule)`

`eps` に関数が渡された場合、`eps(k)` が呼び出され、`action(exploration_policy, on_policy, k, s)` を呼び出すときにイプシロンの値が計算されます。

# フィールド

  * `eps::Function`
  * `rng::AbstractRNG`
  * `m::M` POMDP または MDP の問題
