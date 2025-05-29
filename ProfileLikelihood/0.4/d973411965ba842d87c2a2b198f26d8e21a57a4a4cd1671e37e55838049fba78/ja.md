```
grid_search(prob; save_vals=Val(false), minimise:=Val(false), parallel=Val(false))
```

与えられたグリッドサーチ問題 `prob` に対してグリッドサーチを実行します。

# 引数

  * `prob::GridSearch{F, G}`: グリッドサーチ問題。

# キーワード引数

  * `save_vals:=Val(false)`: 関数値の配列を返すかどうか。
  * `minimise:=Val(false)`: 関数を最小化するか最大化するか。
  * `parallel:=Val(false)`: マルチスレッドでグリッドサーチを実行するかどうか。

# 出力

  * `f_opt`: 最適な目的値。
  * `x_argopt`: `f_opt` を与えたパラメータ。
  * `f_res`: `save_vals==Val(true)` の場合、これは関数値の配列です。
