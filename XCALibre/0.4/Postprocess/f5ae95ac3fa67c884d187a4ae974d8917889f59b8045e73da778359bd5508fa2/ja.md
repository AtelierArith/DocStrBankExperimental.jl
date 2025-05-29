```
pressure_force(patch::Symbol, p::ScalarField, rho)
```

与えられたパッチ/境界に作用する圧力力を計算する関数。

# 入力引数

  * `patch::Symbol` 関心のある境界の名前（`Symbol`として）
  * `p::ScalarField` 圧力場
  * `rho` 密度。非圧縮ソルバーの場合は1に設定します。
