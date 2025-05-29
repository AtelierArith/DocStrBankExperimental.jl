`generator(markov_chain; dt=1)`

# 説明

```
マルコフ連鎖から生成子行列を計算します。
```

# 引数

  * `markov_chain::AbstractVector`: 各時間ステップにおけるマルコフ連鎖の状態を表す整数のベクトル。
  * `dt::Real`: 各状態間の時間ステップ。

# 戻り値

  * `generator_matrix::Matrix`: マルコフ連鎖の生成子行列。
