```
payoff_vector(player, opponent_action)
```

プレイヤーのためのペイオフ値のベクトルを返します。これは2人のゲームにおいて、相手の混合行動に基づく自分の各行動に対するものです。

# 引数

  * `player::Player{2}` : プレイヤーインスタンス。
  * `opponent_action::MixedAction` : 相手の混合行動（実数のベクトル）。

# 戻り値

  * `::Vector` : ペイオフベクトル。
