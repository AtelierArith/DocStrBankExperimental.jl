```julia
create_right_hand_side(
    setup,
    psolver
) -> IncompressibleNavierStokes.var"#right_hand_side#331"

```

```
create_right_hand_side(setup, psolver)
```

与えられたセットアップと圧力ソルバーのためのナビエ-ストークス方程式の右辺を計算する関数を作成します。

# 引数

  * `setup`: グリッドと境界条件を含むシミュレーションセットアップ。
  * `psolver`: 使用される圧力ソルバー。

# 戻り値

ナビエ-ストークス方程式の右辺を計算する関数。
