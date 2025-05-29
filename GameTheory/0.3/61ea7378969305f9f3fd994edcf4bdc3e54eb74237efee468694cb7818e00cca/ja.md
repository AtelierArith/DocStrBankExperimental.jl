```
best_response(player, opponents_actions, payoff_perturbation)
```

`opponents_actions`に対する摂動された最適応答を返します。

# 引数

  * `player::Player` : プレイヤーインスタンス。
  * `opponents_actions::Union{Action,ActionProfile,Nothing}` : N-1人の対戦相手の行動のプロファイル。N=2の場合、実数のベクトル（この場合、対戦相手の混合行動として扱われる）または整数のスカラー（この場合、対戦相手の純粋な行動として扱われる）でなければなりません。N>2の場合、N-1の整数（純粋な行動）またはN-1の実数のベクトル（混合行動）のタプルでなければなりません。（退化ケースN=1の場合、`nothing`でなければなりません。）
  * `payoff_perturbation::Vector{Float64}` : 最適応答を決定する際にペイオフに加えられる値（「ノイズ」）を含む、プレイヤーの行動数と等しい長さのベクトル。

# 戻り値

  * `::Int` : 最適応答行動。
