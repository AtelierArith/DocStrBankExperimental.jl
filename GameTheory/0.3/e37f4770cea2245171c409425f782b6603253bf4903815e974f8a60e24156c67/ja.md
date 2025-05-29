```
payoff_vector(player, opponent_action)
```

プレイヤーのためのペイオフ値のベクトルを返します。これは2人用ゲームにおいて、相手の純粋な行動に対して自分の各行動ごとに1つの値を持ちます。

# 引数

  * `player::Player{2}` : プレイヤーインスタンス。
  * `opponent_action::PureAction` : 相手の純粋な行動（整数）。

# 戻り値

  * `::Vector` : ペイオフベクトル。
