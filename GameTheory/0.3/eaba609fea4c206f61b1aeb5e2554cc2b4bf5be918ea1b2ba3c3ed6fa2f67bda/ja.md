```
best_responses(player, opponents_actions; tol=1e-8)
```

対戦相手の行動に対するすべての最適応答行動を返します。

# 引数

  * `player::Player` : プレイヤーインスタンス。
  * `opponents_actions::Union{Action,ActionProfile,Nothing}` : N-1人の対戦相手の行動のプロファイル。N=2の場合、実数のベクトル（この場合、対戦相手の混合行動として扱われる）または整数のスカラー（この場合、対戦相手の純粋な行動として扱われる）でなければなりません。N>2の場合、N-1の整数（純粋な行動）またはN-1の実数のベクトル（混合行動）のタプルでなければなりません。（退化ケースN=1の場合、`nothing`でなければなりません。）
  * `tol::Real` : 最適応答行動を決定するために使用される許容誤差。

# 戻り値

  * `best_responses::Vector{Int}` : すべての最適応答行動を含むベクトル。
