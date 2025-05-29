```
payoff_vector(player, opponents_actions)
```

N>2 プレイヤーゲームにおけるプレイヤーのペイオフ値のベクトルを返します。自分の各アクションに対して、対戦相手の純粋なアクションのタプルが与えられます。

# 引数

  * `player::Player` : プレイヤーインスタンス。
  * `opponents_actions::PureActionProfile` : N-1 の対戦相手の純粋なアクションのタプル。

# 戻り値

  * `::Vector` : ペイオフベクトル。
