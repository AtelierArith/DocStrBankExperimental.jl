```julia
right_hand_side!(dudt, u, params_ref, t)

```

```
right_hand_side!(dudt, u, params_ref, t)
```

ナビエ-ストークス方程式の右辺をインプレースで計算します。

# 引数

  * `dudt`: 計算された右辺を格納する配列。
  * `u`: 現在の速度場。
  * `params_ref`: セットアップと圧力ソルバーを含むパラメータへの参照。
  * `t`: 現在の時間。

# 戻り値

何も返しません。結果は `dudt` に格納されます。
