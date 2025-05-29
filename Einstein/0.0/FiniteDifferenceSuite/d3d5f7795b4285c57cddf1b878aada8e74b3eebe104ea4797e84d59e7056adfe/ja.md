```
fdm_extrapolation_weights(extrapolation_order::Int, direction::Symbol)
```

左または右の外挿のための重みを生成します。

# 引数

  * `extrapolation_order::Int`: 外挿の次数
  * `direction::Symbol`: 外挿の方向 (:left または :right)

# 戻り値

外挿重みのための整数係数のベクトル。
