```
random_discrete_dp([rng], num_states, num_actions[, beta];
                   k=num_states, scale=1)
```

ランダムに離散動的計画法（DiscreteDP）を生成します。報酬値は平均0、標準偏差`scale`の正規分布から引かれます。

# 引数

  * `rng::AbstractRNG=GLOBAL_RNG` : 擬似乱数生成器。
  * `num_states::Integer` : 状態の数。
  * `num_actions::Integer` : 行動の数。
  * `beta::Real=rand(rng)` : 割引率。指定されていない場合は`[0, 1)`からランダムに選ばれます。
  * `;k::Integer(num_states)` : 各状態-行動ペアに対する次の状態の数。指定されていない場合は`num_states`に等しいです。
  * `scale::Real(1)` : 報酬値の正規分布の標準偏差。

# 戻り値

  * `ddp::DiscreteDP` : DiscreteDPのインスタンス。
