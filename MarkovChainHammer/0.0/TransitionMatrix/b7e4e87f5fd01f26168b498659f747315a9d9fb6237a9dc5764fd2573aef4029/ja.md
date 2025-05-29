sparse*generator(markov*chain; dt = 1)

# 説明

```
スパース形式のマルコフ連鎖から生成行列を計算します
```

# 引数

  * `markov_chain::AbstractVector`: 各時間ステップにおけるマルコフ連鎖の状態を表す整数のベクトル。

# キーワード引数

  * `dt::Real=1`: 構築された演算子の時間ステップ。

# 戻り値

  * `generator_matrix::Matrix`: スパース形式のマルコフ連鎖の生成行列
