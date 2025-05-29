```
is_nash(g, action_profile; tol=1e-8)
```

`action_profile`がナッシュ均衡であればtrueを返します。

# 引数

  * `g::NormalFormGame` : N人のノーマルフォームゲームのインスタンス。
  * `action_profile::ActionProfile` : N個の整数のタプル（純粋な行動）またはN個の実数のベクトル（混合行動）。
  * `tol::Real` : 最適応答行動を決定するために使用される許容誤差。

# 戻り値

  * `::Bool`
