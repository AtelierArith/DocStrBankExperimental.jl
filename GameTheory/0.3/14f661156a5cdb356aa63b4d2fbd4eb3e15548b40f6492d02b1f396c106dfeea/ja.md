```
play!(rng, ld, player_ind, actions)
```

各プレイヤーの選択確率に基づいて、`player_ind`でインデックス付けされたプレイヤーの新しいアクションを返します。

# 引数

  * `rng::AbstractRNG` : 使用される乱数生成器。
  * `ld::LogitDynamics{N}` : `LogitDynamics`インスタンス。
  * `player_ind::Integer` : アクションを取るプレイヤーのインデックス。
  * `actions::Vector{<:Integer}` : アクションプロファイル。

# 戻り値

  * `::Integer` : `player_ind`でインデックス付けされたプレイヤーの新しいアクション。
