`holding_times(markov_chain, number_of_states; dt=1)`

# 説明

```
マルコフ連鎖の保持時間を計算します。
```

# 引数

  * `markov_chain::AbstractVector`: 各時間ステップにおけるマルコフ連鎖の状態を表す整数のベクトル。
  * `number_of_states::Integer`: マルコフ連鎖の状態の数。
  * `dt::Real`: マルコフ連鎖の時間ステップ。

# 戻り値

  * `holding_times::Vector{Vector{Real}}`: 各状態の保持時間のベクトルのベクトル。
