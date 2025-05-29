```
is_nash(g, action; tol=1e-8)
```

1人のプレイヤーを持つ単純なゲームの`action`がナッシュ均衡である場合はtrueを返します。

# 引数

  * `g::NormalFormGame{1}` : 1人プレイヤーのNormalFormGameのインスタンス。
  * `action::Action` : 整数（純粋な行動）または実数のベクトル（混合行動）。
  * `tol::Float64` : 最適応答行動を決定するために使用される許容誤差。

# 戻り値

  * `::Bool`

```
