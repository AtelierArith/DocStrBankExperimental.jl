```
payoff_vector(player, opponent_action)
```

プレイヤーのためのペイオフ値のベクトルを返します。これは、1人のプレイヤーのトリビアルゲームにおける各自のアクションに対して1つずつです。

# 引数

  * `player::Player{1}` : プレイヤーインスタンス。
  * `opponent_action::Nothing`

# 戻り値

  * `::Vector` : ペイオフベクトル。

```
